---
title: 软件Recommendations
description: 查看与Adobe Commerce部署和Magento Open Source部署的最佳性能相关的推荐软件列表。
source-git-commit: 8572cc8702d6f7e9c40b64110a9ba18aa5784f44
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 0%

---


# 软件建议

对于的生产实例，我们需要以下软件 [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx和 [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] 或OpenSearch](../installation/prerequisites/search-engine/overview.md)

对于多服务器部署，或者对于计划扩展其业务的商户，我们建议执行以下操作：

* [[!DNL Varnish] 缓存](../configuration/cache/config-varnish.md)
* [雷迪斯](../configuration/cache/redis-session.md) （从2.0.6+版）
* 作为 [默认缓存](../configuration/cache/redis-pg-cache.md) （请勿将此实例用于页面缓存）

请参阅 [系统要求](../installation/system-requirements.md) 有关每种软件类型支持的版本的信息。

## 操作系统

操作系统配置和优化与 [!DNL Commerce] 与其他高负载web应用程序相比。 随着服务器处理的并发连接数的增加，可用套接字的数量可能会被完全分配。 Linux内核支持“重用”TCP连接的机制。 要启用此机制，请在 `/etc/sysctl.conf`:

>[!INFO]
>
>启用net.ipv4.tcp_tw_reuse对传入连接没有影响。

```text
net.ipv4.tcp_tw_reuse = 1
```

内核参数 `net.core.somaxconn` 控制等待连接的打开套接字的最大数量。 此值可以安全地增加到1024，但应与服务器处理此量的能力相关联。 要启用此内核参数，请在 `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Magento完全支持PHP 7.3和7.4。配置PHP时，需考虑以下几个因素，以便在请求处理方面获得最大速度和效率。

### PHP扩展

我们建议将活动PHP扩展的列表限制为 [!DNL Commerce] 功能。

Magento Open Source和Adobe Commerce:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* ext-sockets
* ext-na
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

此外，Adobe Commerce要求：

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* ext-sockets
* ext-na
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

添加更多扩展会增加库加载时间。

>[!INFO]
>
>`php-mcrypt` 已从PHP 7.2中删除，并替换为 [`sodium` 库](https://www.php.net/manual/en/book.sodium.php). 确保 [钠](https://www.php.net/manual/en/sodium.installation.php) 升级PHP时正确启用。

>[!INFO]
>
>任何分析和调试扩展的存在都可能会对页面的响应时间产生负面影响。 例如，没有任何调试会话的活动xDebug模块可将页面响应时间增加多达30%。

### PHP设置

确保成功执行所有 [!DNL Commerce] 在不将数据或代码转储到磁盘的情况下，按如下方式设置内存限制：

```text
memory_limit=1G
```

对于调试，请将此值增加到2G。

#### Realpath_cache配置

改进 [!DNL Commerce] 性能，添加或更新以下建议的内容 `realpath_cache` 设置 `php.ini` 文件。 此配置允许PHP进程缓存指向文件的路径，而不是每次加载页面时都查找它们。 请参阅 [性能优化](https://www.php.net/manual/en/ini.core.php) （在PHP文档中）。

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

从 [!DNL Commerce] 在PHP 7中，必须激活OpCache模块并正确配置该模块。 建议为模块设置以下设置：

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

在微调opcache的内存分配时，请考虑Magento代码库的大小和所有扩展。 Magento的性能团队使用上例中的值进行测试，因为它在opcache中提供了足够的空间来容纳平均已安装的扩展数。

如果您的计算机内存不足，并且未安装许多扩展或自定义设置，请使用以下设置获得类似结果：

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

我们建议启用 [PHP APCu扩展](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) 和 [配置 `composer` 支持它](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) 以优化性能。 此扩展会缓存已打开文件的文件位置，这会提高 [!DNL Commerce] 服务器调用，包括页面、Ajax调用和端点。

编辑 `apcu.ini` 文件以包含以下内容：

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Web服务器

Magento完全支持Nginx和Apache Web服务器。 [!DNL Commerce] 在  `<magento_home>/nginx.conf.sample` (Nginx)和  `<magento_home>.htaccess.sample` (Apache)文件。  Nginx示例包含用于提高性能的设置，并且经过设计，因此无需重新配置。 在样例文件中定义的一些主要配置最佳实践包括：

* 用于在浏览器中缓存静态内容的设置
* PHP的内存和执行时间设置
* 内容压缩设置

您还应配置用于处理输入请求的线程数，如下所示：

| Web服务器 | 属性名称 | 位置 | 相关信息 |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [调整NGINX以实现性能](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache性能调整](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache MPM通用指令](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

本文档不提供深入信息 [!DNL MySQL] 调整说明，因为每个商店和环境都不同，但我们可以提出一些一般建议。

在 [!DNL MySQL] 5.7.9我们有信心 [!DNL MySQL] 具有良好的默认设置。 最关键的设置包括：

| 参数 | 默认 | 描述 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | 默认值设置为8，以避免多线程尝试访问同一实例时出现问题。 |
| `innodb_buffer_pool_size` | 128MB | 与上述多个池实例结合使用，这意味着默认内存分配为1024 MB。 总大小在所有缓冲池中进行划分。 为获得最佳效率，请指定 `innodb_buffer_pool_instances` 和 `innodb_buffer_pool_size` 这样每个缓冲池实例至少为1 GB。 |
| `max_connections` | 150 | 的值 `max_connections` 参数应与应用程序服务器中配置的PHP线程总数相关联。 一般性建议为300个小型，1 000个中型环境。 |
| `innodb_thread_concurrency` | 0 | 此配置的最佳值应使用公式计算： `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento强烈建议使用 [!DNL Varnish] 作为存储的完整页面缓存服务器。 PageCache模块仍位于代码库中，但应仅将其用于开发目的。 它不应与（或）一起使用， [!DNL Varnish].

安装 [!DNL Varnish] 在Web层前面的单独服务器上。 它应接受所有传入请求并提供缓存的页面副本。 允许 [!DNL Varnish] 为了有效地处理安全页面，可以将SSL终止代理放置在 [!DNL Varnish]. Nginx可用于此目的。

[!DNL Commerce] 分发示例配置文件 [!DNL Varnish] （版本4和5），其中包含所有推荐的性能设置。 其中，性能方面最关键的是：

* **后端运行状况检查** 民调 [!DNL Commerce] 服务器来确定它是否及时响应。
* **宽限模式** 允许您指示 [!DNL Varnish] 将缓存中的对象保留在其生存时间(TTL)期限之后，并在 [!DNL Commerce] 不正常，或者尚未获取新内容。
* **Saint模式** 黑名单不健康 [!DNL Commerce] 服务器的可配置时间。 因此，在使用 [!DNL Varnish] 作为负载平衡器。

请参阅 [高级 [!DNL Varnish] 配置](../configuration/cache/config-varnish-advanced.md) 有关实施这些功能的更多信息。

### 优化资产性能

通常，我们建议将您的资产（图像、JS、CSS等）存储在CDN上，以获得最佳性能。

如果您的网站不需要部署大量区域设置，并且您的服务器与大多数客户位于同一区域，则通过将资产存储在 [!DNL Varnish] 而不是使用CDN。

要将资产存储在 [!DNL Varnish]，在 `default.vcl` 文件生成者 [!DNL Commerce] 表示 [!DNL Varnish] 5.

在 `if` 中用于清除请求的语句 `vcl_recv` 子程序，添加：

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

在 `vcl_backend_response` 子程序，查找 `if` 用于取消设置Cookie的语句 `GET` 或 `HEAD` 请求。
已更新 `if` 块应如下所示：

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

重新启动 [!DNL Varnish] 服务器来刷新缓存的资产。

## 缓存和会话服务器

Magento提供了许多用于存储缓存和会话数据的选项，包括Redis、Memcache、文件系统和数据库。 下面将讨论其中一些选项。

### 单个Web节点设置

如果您计划仅使用一个Web节点来提供所有流量，则将缓存放在远程Redis服务器上是没有意义的。 而是使用文件系统或本地Redis服务器。 如果要使用文件系统，请将缓存文件夹放在RAM文件系统上装入的卷上。 如果您想使用本地Redis服务器，我们强烈建议配置Redis，以便它使用套接字进行直接连接，而不是通过HTTP交换数据。

### 设置多个Web节点

对于设置多个Web节点，Redis是最佳选项。 因为 [!DNL Commerce] 主动缓存大量数据以获得更好的性能，请注意网络节点与Redis服务器之间的网络通道。 您不希望渠道成为请求处理的瓶颈。

>[!INFO]
>
>如果您需要同时提供数以百计的请求，则可能需要一个多达1 Gbit（甚至更宽）的通道来连接您的Redis服务器。
