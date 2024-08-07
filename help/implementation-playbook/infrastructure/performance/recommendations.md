---
title: 性能优化建议
description: 按照以下建议优化Adobe Commerce实施性能。
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
feature: Cloud
topic: Performance
source-git-commit: 8b09d734d8ac4490cd88af5673acd0a41b6cdf66
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 0%

---


# 性能优化审查

尽管性能优化可能来自许多方面，但对于大多数场景，仍有一些需要考虑的一般建议。 一般建议包括基础架构元素的配置优化、Adobe Commerce后端配置和架构可扩展性规划。

>[!TIP]
>
>有关性能优化的详细信息，请参阅&#x200B;[_性能最佳实践指南_](../../../performance/overview.md)。

## 基础架构

以下各节介绍了基础架构优化的建议。

### DNS查找

DNS查找是查找域名所属的IP地址的过程。 浏览器必须等待DNS查找完成，然后才能下载每个请求的任何内容。 减少DNS查找对于改善总体页面加载时间非常重要。

### 内容交付网络(CDN)

使用CDN优化资源下载性能。 Adobe Commerce使用Fastly。 如果您有Adobe Commerce的内部实施，则还应当考虑添加CDN层。

### Web延迟

数据中心的位置会影响前端用户的Web延迟。

### 网络带宽

充足的网络带宽是Web节点、数据库、缓存/会话服务器和其他服务之间数据交换的关键要求之一。

由于Adobe Commerce有效地使用缓存来实现高性能，因此您的系统可以主动与缓存服务器（如Redis）交换数据。 如果Redis安装在远程服务器上，则必须在Web节点和缓存服务器之间提供充足的网络通道，以防止读/写操作出现瓶颈。

### 操作系统(OS)

与其他高负载Web应用程序相比，Adobe Commerce的操作系统配置和优化是相似的。 随着服务器处理的并发连接数的增加，可用套接字的数量可以完全分配。

### Web节点的CPU

一个CPU核心可以有效地处理大约2 - 4个Adobe Commerce请求，而无需使用缓存。 要确定需要多少个Web节点/核心来处理所有传入请求而不将其放入队列，请使用以下公式：

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### PHP-FPM设置

优化这些设置取决于不同项目的性能测试结果。

- **ByteCode** — 要在PHP 7上实现Adobe Commerce的最大速度，必须激活`opcache`模块并正确对其进行配置。

- **APCU**—Adobe建议启用PHP APCu扩展并配置Composer以优化最大性能。 此扩展可缓存已打开文件的文件位置，从而提高用于Adobe Commerce服务器调用（包括页面、Ajax调用和端点）的性能。

- **Realpath_cacheconfiguration** — 优化`realpath_cache`允许PHP进程缓存文件的路径，而不是在每次加载页面时查找文件。

### Web服务器

使用nginx作为Web服务器只需要少量重新配置。 使用Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample))中的示例配置文件，nginx Web服务器可提供更好的性能并易于配置。

- 使用TCP正确设置PHP-FPM

- 启用HTTP/2和Gzip

- 优化工作程序连接

### 数据库

本文档没有提供深入的MySQL优化说明，因为每个存储区和环境各不相同，但Adobe可以提出一般建议。

Adobe Commerce数据库（以及任何其他数据库）对可用于存储数据和索引的内存量敏感。 要有效地使用MySQL数据索引，可用的内存量至少应接近数据库中存储的数据大小的一半。

优化`innodb_buffer_pool_instances`设置，以避免多个线程尝试访问同一实例时出现问题。 `max_connections`参数的值应与应用程序服务器中配置的PHP线程总数相关。 使用以下公式计算`innodb-thread-concurrency`的最佳值：

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### 会话缓存

会话缓存是为Redis的单独实例配置的良好候选项。 此缓存类型的内存配置应考虑站点的购物车放弃策略以及会话预计在缓存中保留的时长。

Redis应分配足够的内存来保存内存中的所有其他缓存，以获得最佳性能。 块缓存是决定要配置的内存量的关键因素。 块缓存会相对于网站上的页面数量（SKU数量x商店查看数量）而增长。

### 页面缓存

Adobe强烈建议在Adobe Commerce商店中使用Varnish进行全页缓存。 `PageCache`模块仍存在于代码库中，但应仅将其用于开发目的。

在Web层前面的单独服务器上安装Varnish。 它应接受所有传入请求并提供缓存的页面副本。 为了允许Varnish有效地处理安全页面，可以将SSL终止代理放置在Varnish之前。 Nginx可用于此目的。

虽然Varnish全页缓存内存失效有效，但Adobe建议为Varnish分配足够的内存，以便在内存中保存最常用的页。

### 消息队列

Message Queue Framework (MQF)是一个允许模块将消息发布到队列的系统。 它还定义了异步接收消息的消费者。 Adobe Commerce支持[!DNL RabbitMQ]作为消息代理，该消息代理为发送和接收消息提供了一个可扩展的平台。

### 性能测试和监控

我们始终建议在每个生产版本之前进行性能测试，以估算电子商务平台的功能。 启动后持续监控，并针对处理高峰期制定可扩展性和备份计划。

>[!NOTE]
>
> 云基础架构上的Adobe Commerce已应用上述基础架构和架构优化，但DNS查找除外，因为它超出了范围。

### Search {#search-heading}

从Adobe Commerce版本2.4开始，需要Elasticsearch（或OpenSearch），但也是为2.4之前的版本启用它的最佳实践。

## 操作模型

除了前面提到的通用基础架构优化建议外，还有一些方法可用于增强特定业务模式和规模的性能。 本文档没有针对所有这些方案提供深入的优化说明，因为每种方案各不相同，但Adobe会提供一些高级选项供您参考。

### Headless体系结构

有一个专用于[headless](../../architecture/enterprise-blueprint.md#headless-storefront)的单独部分。 总之，它将店面层与平台本身隔离开来。 它仍然是相同的后端，但Adobe Commerce不再直接处理请求，而是仅通过GraphQL API支持自定义店面。

### 保持Adobe Commerce更新

Adobe Commerce在运行最新版本时始终表现更好。 即使在每个新版本发布后无法使Adobe Commerce保持最新，仍建议在Adobe Commerce引入显着的性能优化时[升级](../../../upgrade/overview.md)。

例如，2020年，Adobe发布了对Redis层的优化，修复了许多低效率、连接问题以及Redis和Adobe Commerce之间不必要的数据传输。 2.3和2.4之间的总体性能是昼夜不停的，并且由于Redis优化，在购物车、结账、并发用户方面得到了显着改进。

### 优化数据模型

许多问题源自数据，包括错误的数据模型、结构不正确的数据以及缺少索引的数据。

如果您正在测试一些连接，看起来可能会很有帮助，但在部署到生产环境后，您可能会看到性能严重下降。 系统集成商了解如何设计数据模型（特别是产品属性）、避免添加不必要的属性以及保留影响业务逻辑的强制属性（如定价、库存可用性和搜索）非常重要。

对于那些不会影响业务逻辑但仍必须存在于店面中的属性，将它们组合为几个属性（例如，JSON格式）。

为优化平台性能，如果店面不需要基于从PIM或ERP获取的数据或属性的业务逻辑，则无需将该属性添加到Adobe Commerce中。

### 可扩展性设计

对于开展营销活动且经常面临流量高峰期的企业而言，可扩展性非常重要。 可扩展的体系结构和应用程序设计可以在高峰期增加资源，并在高峰期后减少资源。
