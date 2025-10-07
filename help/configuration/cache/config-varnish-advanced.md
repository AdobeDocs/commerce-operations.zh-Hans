---
title: 高级清漆配置
description: 了解如何为Adobe Commerce配置高级清漆功能，包括运行状况检查、宽限和saint模式。 了解VCL优化技术。
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# 高级清漆配置

Varnish提供了多项功能，可在Commerce服务器无法正常运行时防止客户遇到长时间延迟和超时。 可在`default.vcl`文件中配置这些功能。 本主题介绍Commerce在您从管理员下载的VCL（清漆配置语言）文件中提供的附加内容。

有关使用清漆配置语言的详细信息，请参阅[清漆参考手册](https://varnish-cache.org/docs/index.html)。

## 运行状况检查

Varnish运行状况检查功能可轮询Commerce服务器以确定它是否及时响应。 如果它响应正常，则会在生存时间(TTL)期限过期后重新生成新内容。 否则，Varnish将始终提供过时的内容。

Commerce定义了以下默认运行状况检查：

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

此运行状况检查每5秒调用一次`pub/health_check.php`脚本。 此脚本检查服务器、每个数据库和Redis（如果已安装）的可用性。 脚本必须在2秒内返回响应。 如果脚本确定这些资源中有任何已关闭，则会返回500 HTTP错误代码。 如果每10次尝试中就有6次收到此错误代码，则后端被视为不正常。

`health_check.php`脚本位于`pub`目录中。 如果您的Commerce根目录为`pub`，请务必将`url`参数中的路径从`/pub/health_check.php`更改为`health_check.php`。

有关详细信息，请参阅[清漆运行状况检查](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks)文档。

## 宽限模式

宽限模式允许Varnish将缓存中的对象保留在超出其TTL值的范围内。 然后，清漆可在获取新版本时提供过期（过时）的内容。 这可以改善通信流量并减少加载时间。 它用于以下情况：

- 当Commerce后端运行正常，但请求所花费的时间比正常时间更长时
- 当Commerce后端不正常时。

`vcl_hit`子例程定义Varnish如何响应已缓存对象的请求。

### 当Commerce后端运行状况良好时

当运行状况检查确定Commerce后端运行状况良好时，Varnish会检查时间是否在宽限期内。 默认宽限期为300秒，但商家可以从管理员设置值，如[配置Commerce以使用Varnish](configure-varnish-commerce.md)中所述。 如果宽限期未过期，则Varnish会提供过时的内容，并从Commerce服务器异步刷新对象。 如果宽限期已过，则Varnish会提供过时内容，并从Commerce后端同步刷新对象。

Varnish提供过时对象的最大时间是宽限期（默认为300秒）和TTL值(默认为86400秒)之和。

要从`default.vcl`文件中更改默认宽限期，请编辑`vcl_hit`子例程中的以下行：

```conf
if (obj.ttl + 300s > 0s) {
```

### 当Commerce后端不正常时

如果Commerce后端无响应，则Varnish会从缓存中提供三天的过期内容（或如`beresp.grace`中的定义）以及剩余的TTL（默认情况下为一天），除非手动清除缓存的内容。

## Saint模式

Saint模式会在可配置的时间内排除不正常的后端。 因此，在使用Varnish作为负载平衡器时，不健康的后端将无法提供流量。 Saint模式可与宽限期模式一起使用，以允许复杂地处理不正常的后端服务器。 例如，如果一个后端服务器不正常，可以将重试路由到另一个服务器。 如果所有其他服务器都停机，则提供过时的缓存对象。 在`default.vcl`文件中定义了saint模式后端主机和封锁期。

当单独使Commerce实例离线以执行维护和升级任务而不影响Commerce站点的可用性时，也可以使用Saint模式。

### Saint模式先决条件

指定一个计算机作为主安装。 在此计算机上，安装Commerce的主实例、mySQL数据库和Varnish。

在所有其他计算机上，Commerce实例必须能够访问主计算机的mySQL数据库。 辅助计算机还应该可以访问主Commerce实例的文件。

或者，可以在所有计算机上关闭静态文件版本控制。 可从&#x200B;**商店** >设置> **配置** > **高级** > **开发人员** > **静态文件设置** > **签名静态文件** = **否**&#x200B;下的管理员访问它。

最后，所有Commerce实例都必须处于生产模式。 在Varnish开始之前，清除每个实例上的缓存。 在管理员中，转到&#x200B;**系统** >工具> **缓存管理**，然后单击&#x200B;**刷新Magento缓存**。 您还可以运行以下命令来清除缓存：

```bash
bin/magento cache:flush
```

### 安装

Saint模式不是主Varnish包的一部分。 必须下载并安装该版本`vmod`。 因此，必须从源重新编译Varnish，如您的Varnish版本的[安装说明](https://varnish-cache.org/docs/index.html)中所述。

重新编译后，可以安装Saint模式模块。 一般来说，请按照以下步骤操作：

1. 从[Varnish模块](https://github.com/varnish/varnish-modules)获取源代码。 克隆Git版本（主版本），因为0.9.x版本包含源代码错误。
1. 使用autotools构建源代码：

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

有关安装Saint模式模块的信息，请参阅[清漆模块集合](https://github.com/varnish/varnish-modules)。

### 示例VCL文件

以下代码示例显示了要启用saint模式必须添加到VCL文件中的代码。 将`import`语句和`backend`定义放在文件的顶部。

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
