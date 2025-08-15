---
title: 软件建议
description: 查看与Adobe Commerce部署的最佳性能相关的推荐软件列表。
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# 软件推荐

我们需要以下软件用于[!DNL Commerce]的生产实例：

* [PHP](../installation/system-requirements.md)
* Nginx和[PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch]或OpenSearch](../installation/prerequisites/search-engine/overview.md)

对于多服务器部署或计划扩展业务的商家，我们建议执行以下操作：

* [[!DNL Varnish]缓存](../configuration/cache/config-varnish.md)
* 会话的[Redis](../configuration/cache/redis-session.md)（从2.0.6+开始）
* 单独的Redis实例作为[默认缓存](../configuration/cache/redis-pg-cache.md)（不要将此实例用于页面缓存）

有关每种类型软件支持版本的信息，请参阅[系统要求](../installation/system-requirements.md)。

## 操作系统

[!DNL Commerce]的操作系统配置和优化与其他高负载Web应用程序类似。 随着服务器处理的并发连接数的增加，可用套接字的数量可以完全分配。 Linux内核支持“重用”TCP连接的机制。 要启用此机制，请在`/etc/sysctl.conf`中设置以下值：

>[!INFO]
>
>启用net.ipv4.tcp_tw_reuse对传入连接没有影响。

```text
net.ipv4.tcp_tw_reuse = 1
```

内核参数`net.core.somaxconn`控制等待连接的打开套接字的最大数目。 可以安全地将此值增加到1024，但应该将其与服务器处理此数量的能力相关联。 要启用此内核参数，请在`/etc/sysctl.conf`中设置以下值：

```text
net.core.somaxconn = 1024
```

## PHP

Magento完全支持PHP 7.3和7.4。在配置PHP以获得最大请求处理速度和效率时，需要考虑以下几个因素。

### PHP扩展

我们建议将活动PHP扩展的列表限制为[!DNL Commerce]功能所需的那些扩展。

Magento Open Source和Adobe Commerce：

* ext-bcmath
* ext-ctype
* 外部卷曲
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
* 外部soap
* 分插座
* 外钠
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

此外，Adobe Commerce要求：

* ext-bcmath
* ext-ctype
* 外部卷曲
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
* 外部soap
* 分插座
* 外钠
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
>已从PHP 7.2中删除`php-mcrypt`并将其替换为[`sodium`库](https://www.php.net/manual/en/book.sodium.php)。 请确保在升级PHP时正确启用[钠](https://www.php.net/manual/en/sodium.installation.php)。

>[!INFO]
>
>任何分析和调试扩展的存在都可能会对页面的响应时间产生负面影响。 例如，不带任何调试会话的活动xDebug模块最多可将页面响应时间增加30%。

### PHP设置

要确保成功执行所有[!DNL Commerce]实例，而不将数据或代码转储到磁盘，请按照以下方式设置内存限制：

```text
memory_limit=1G
```

对于调试，请将此值增加到2G。

#### Realpath_cache配置

要提高[!DNL Commerce]性能，请在`realpath_cache`文件中添加或更新以下推荐的`php.ini`设置。 此配置允许PHP进程缓存文件的路径，而不是在每次加载页面时查找它们。 请参阅PHP文档中的[性能调整](https://www.php.net/manual/en/ini.core.php)。

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### 字节代码

要在PHP 7上获得[!DNL Commerce]的最大速度，您必须激活OpCache模块并正确对其进行配置。 建议为模块设置以下设置：

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

在微调opcache的内存分配时，请考虑Magento代码库和您的所有扩展的大小。 Magento的性能团队使用前面的示例中的值进行测试，因为它在opcache中提供了足够的空间来容纳平均已安装的扩展数。

如果您的计算机内存不足，但未安装许多扩展或自定义设置，请使用以下设置获得类似结果：

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

我们建议启用[PHP APCu扩展](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache)和[配置`composer`以支持它](../performance/deployment-flow.md#preprocess-dependency-injection-instructions)以优化其最大性能。 此扩展缓存已打开文件的文件位置，这将提高[!DNL Commerce]服务器调用（包括页面、Ajax调用和端点）的性能。

编辑您的`apcu.ini`文件以包含以下内容：

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Web服务器

Magento完全支持Nginx和Apache Web服务器。 [!DNL Commerce]在`<magento_home>/nginx.conf.sample` (Nginx)和`<magento_home>.htaccess.sample` (Apache)文件中提供了示例推荐配置文件。  Nginx示例包含用于提高性能的设置，并且设计得只需很少的重新配置。 示例文件中定义的一些主要配置最佳实践包括：

* 在浏览器中缓存静态内容的设置
* PHP的内存和执行时间设置
* 内容压缩设置

您还应配置用于输入请求处理的线程数，如下所示：

| Web服务器 | 属性名称 | 位置 | 相关信息 |
|--- | --- | --- | ---|
| 恩金克斯 | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [调整NGINX以提高性能](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache性能调整](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache MPM公共指令](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

本文档未提供深入的[!DNL MySQL]优化说明，因为每个存储和环境都不同，但我们可以提出一些常规建议。

对[!DNL MySQL] 5.7.9进行了许多改进。我们确信已使用良好的默认设置分发[!DNL MySQL]。 最关键的设置是：

| 参数 | 默认 | 描述 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | 默认值为8，以避免多个线程尝试访问同一实例时出现问题。 |
| `innodb_buffer_pool_size` | 128兆字节 | 结合上述多个池实例，这意味着默认内存分配为1024MB。 总大小在所有缓冲池中分配。 为获得最佳效率，请指定`innodb_buffer_pool_instances`和`innodb_buffer_pool_size`的组合，以便每个缓冲池实例至少为1 GB。 |
| `max_connections` | 150 | `max_connections`参数的值应与应用程序服务器中配置的PHP线程总数相关。 一般建议是，小环境为300，中环境为1,000。 |
| `innodb_thread_concurrency` | 0 | 此配置的最佳值应按以下公式计算： `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento强烈建议使用[!DNL Varnish]作为商店的整页缓存服务器。 PageCache模块仍存在于代码库中，但应仅将其用于开发目的。 它不应与[!DNL Varnish]一起使用，也不应替代。

在Web层前面的单独服务器上安装[!DNL Varnish]。 它应接受所有传入请求并提供缓存的页面副本。 为了允许[!DNL Varnish]有效地处理安全页面，可以将SSL终止代理置于[!DNL Varnish]之前。 Nginx可用于此目的。

[!DNL Commerce]为[!DNL Varnish]（版本4和5）分发一个示例配置文件，其中包含所有推荐的性能设置。 其中最重要的性能包括：

* **后端运行状况检查**&#x200B;轮询[!DNL Commerce]服务器以确定它是否及时响应。
* **宽限模式**&#x200B;允许您指示[!DNL Varnish]在超出[!DNL Commerce]的生存时间(TTL)时段后保留缓存中的对象并提供此过时内容（如果不正常或尚未获取新内容）。
* **Saint模式**&#x200B;在可配置的时间范围内将不正常的[!DNL Commerce]服务器列入黑名单。 因此，当使用[!DNL Varnish]作为负载平衡器时，不正常的后端无法提供流量。

有关实现这些功能的详细信息，请参阅[高级 [!DNL Varnish] 配置](../configuration/cache/config-varnish-advanced.md)。

### 优化资产性能

通常，我们建议将您的资产（图像、JS、CSS等）存储在CDN上以获得最佳性能。

如果您的网站不需要部署大量区域设置，并且您的服务器与大多数客户位于同一区域，则通过将资产存储在[!DNL Varnish]中而不是使用CDN，您可能会发现以较低的成本获得了显着的性能提升。

要将您的资产存储在[!DNL Varnish]中，请在`default.vcl`为[!DNL Commerce] 5生成的[!DNL Varnish]文件中添加以下VCL条目。

在`if`子例程中PURGE请求的`vcl_recv`语句的末尾，添加：

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

在`vcl_backend_response`子例程中，查找用于为`if`或`GET`请求取消设置Cookie的`HEAD`语句。
更新的`if`块应如下所示：

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

每次升级网站或部署/更新资产时，请重新启动[!DNL Varnish]服务器以刷新缓存的资产。

## 缓存和会话服务器

Magento提供了多个选项来存储缓存和会话数据，包括Redis、Memcache、文件系统和数据库。 下面将讨论其中一些选项。

### 单个Web节点设置

如果您计划仅使用一个Web节点提供所有流量，则将缓存放在远程Redis服务器上没有任何意义。 而是使用文件系统或本地Redis服务器。 如果要使用文件系统，请将缓存文件夹放在RAM文件系统上装入的卷上。 如果要使用本地Redis服务器，我们强烈建议配置Redis，使其使用套接字进行直接连接，而不是通过HTTP交换数据。

### 多个Web节点设置

对于多Web节点设置，Redis是最佳选项。 由于[!DNL Commerce]主动缓存大量数据以获得更好的性能，请注意网络节点和Redis服务器之间的网络通道。 您不希望该渠道成为请求处理的瓶颈。

>[!INFO]
>
>如果您需要同时处理成百上千个请求，则可能需要一个高达1 GB（或更宽）的通道来连接Redis服务器。
