---
title: 高级清漆配置
description: 配置高级清漆功能，包括运行状况检查、宽限和saint模式。
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# 高级清漆配置

清漆提供了几项功能，可防止客户在商务服务器无法正常运行时遇到长时间延迟和超时。 这些功能可以在 `default.vcl` 文件。 本主题介绍Commerce在从管理员下载的VCL（清漆配置语言）文件中提供的新增内容。

请参阅 [清漆参考手册](https://varnish-cache.org/docs/6.3/reference/index.html) 有关使用清漆配置语言的详细信息。

## 运行状况检查

清漆运行状况检查功能会轮询商务服务器以确定它是否及时响应。 如果响应正常，则在生存时间(TTL)期限过期后重新生成新内容。 如果没有，清漆总是提供陈旧的内容。

商务定义以下默认运行状况检查：

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

每5秒，此运行状况检查会调用 `pub/health_check.php` 脚本。 此脚本检查服务器、每个数据库和Redis（如果已安装）的可用性。 脚本必须在2秒内返回响应。 如果脚本确定其中任何资源已关闭，则会返回500 HTTP错误代码。 如果在每次10次尝试中收到此错误代码，则 [后端](https://glossary.magento.com/backend) 被认为不健康。

的 `health_check.php` 脚本位于 `pub` 目录访问Advertising Cloud的帮助。 如果您的商务根目录为 `pub`，请务必在 `url` 参数自 `/pub/health_check.php` to `health_check.php`.

有关更多信息，请参阅 [清漆运行状况检查](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) 文档。

## 宽限模式

宽限模式允许清漆将对象保留在 [缓存](https://glossary.magento.com/cache) 超出其TTL值。 清漆可在获取新版本时提供过期（过时）的内容。 这可改善流量并减少加载时间。 它适用于以下情况：

- 当商务后端运行正常，但请求花费的时间比正常时间长时
- 当商务后端不正常时。

的 `vcl_hit` 子例程定义清漆如何响应已缓存对象的请求。

### 当商务后端运行正常时

当运行状况检查确定商务后端运行正常时，清漆检查时间是否在宽限期内。 默认宽限期为300秒，但商户可以从 [管理员](https://glossary.magento.com/admin) 如 [配置商务以使用清漆](config-varnish-magento.md). 如果宽限期未过期，清漆将提供过时的内容，并从商务服务器异步刷新对象。 如果宽限期已过，清漆将提供过时的内容，并从Commerce后端同步刷新对象。

清漆提供过时对象的最大时间是宽限期（默认为300秒）和TTL值(默认为86400秒)的总和。

要在 `default.vcl` ，请在 `vcl_hit` 子程序：

```conf
if (obj.ttl + 300s > 0s) {
```

### 当商务后端不正常时

如果商务后端没有响应，则清漆会从缓存中提供三天(或根据 `beresp.grace`)加上剩余的TTL（默认为一天），除非手动清除缓存的内容。

## Saint模式

Saint模式在可配置的时间内排除不正常的后端。 因此，在将清漆用作负载平衡器时，不正常的后端无法提供流量。 Saint模式可与宽限模式一起使用，以便能够复杂地处理不正常的后端服务器。 例如，如果一个后端服务器不正常，则可以将重试路由到另一个服务器。 如果所有其他服务器都关闭，则提供过时的缓存对象。 在 `default.vcl` 文件。

当商务实例单独脱机以执行维护和升级任务而不影响商务网站的可用性时，也可以使用SAINT模式。

### Saint模式先决条件

指定一台计算机作为主安装。 在此计算机上，安装Commerce、mySQL数据库和Riest的主实例。

在所有其他计算机上，商务实例必须具有访问主计算机的mySQL数据库的权限。 辅助计算机还应有权访问主Commerce实例的文件。

或者， [静态文件](https://glossary.magento.com/static-files) 可以在所有计算机上关闭版本控制。 可从下方的管理员访问此设置 **商店** >设置> **配置** > **高级** > **开发人员** > **静态文件设置** > **对静态文件进行签名** = **否**.

最后，所有商务实例都必须处于生产模式。 在清漆开始之前，清除每个实例上的缓存。 在管理员中，转到 **系统** >工具> **缓存管理** 单击 **刷新Magento缓存**. 您还可以运行以下命令以清除缓存：

```bash
bin/magento cache:flush
```

### 安装

Saint模式不是主清漆包的一部分。 它是单独版本控制的 `vmod` 必须下载和安装的。 因此，应从源中重新编译清漆，如以下文章所述：

- [安装清漆6.4](https://varnish-cache.org/docs/6.4/installation/install.html)
- [安装清漆6.0](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

重新编译后，您可以安装Saint模式 [模块](https://glossary.magento.com/module). 通常，请执行以下步骤：

1. 从获取源代码 [清漆模块](https://github.com/varnish/varnish-modules). 克隆Git版本(主控版本)，因为0.9.x版本包含源代码错误。
1. 使用自动工具构建源代码：

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

请参阅 [清漆模组集合](https://github.com/varnish/varnish-modules) 有关安装Saint模式模块的信息。

### 示例VCL文件

以下代码示例显示了必须添加到VCL文件中才能启用saint模式的代码。 将 `import` 报表和 `backend` 定义。

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
