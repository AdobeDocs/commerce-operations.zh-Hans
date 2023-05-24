---
title: 参考架构
description: 查看Adobe Commerce和Magento Open Source部署中推荐的参考架构的示意图。
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# 参考架构

本主题介绍了一般性建议设置，适用于Adobe Commerce和Magento Open Source实例，这些实例使用在数据中心物理托管（非虚拟化）的普通服务器，其中资源不与其他用户共享。 您的托管提供商（尤其是专门从事Commerce高性能托管业务的提供商）可能建议采用对您的要求同样有效或更为有效的其他设置。

有关云基础架构环境上的Adobe Commerce，请参阅 [入门级架构](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] 参考架构图

此 [!DNL Commerce] 参考体系结构图代表了设置可扩展架构的最佳实践方法 [!DNL Commerce] 站点。

图中每个元素的颜色指示该元素是Magento Open Source还是Adobe Commerce的一部分，以及是否必需。

* Magento Open Source需要橙色元素
* 灰色元素对于Magento Open Source是可选的
* 蓝色元素是Adobe Commerce的可选元素

![Commerce参考架构图](../assets/performance/images/ref-architecture-2.3.png)

以下部分提供了有关Commerce参考架构图每个部分的建议和注意事项。

### [!DNL Varnish]

* A [!DNL Varnish] 群集可以根据站点的流量进行扩展
* 根据所需的缓存页数优化实例大小
* 在高流量网站上，使用 [!DNL Varnish] 主控确保每个Web层缓存刷新一个请求（最多）

### Web

* 为流量和冗余启用节点扩展
* 一个节点主控并运行cron
* 或者，使用专用的管理员和工作者节点

### 缓存

* 考虑为会话实施单独的Redis实例
* 每个缓存可以有一个Redis实例
* 将实例大小设置为包含预期的最大缓存大小

### 数据库和队列

* 高流量站点可以使用从属数据库调整数据库性能，并为订单/购物车拆分数据库(在Adobe Commerce中)
* 考虑使用从数据库实现快速恢复并用于数据备份
* 低流量站点可以将图像存储在数据库中

### 搜索 {#search-heading}

* 根据搜索流量调整实例数

### 存储

* 考虑将GFS或GlusterFS用于发布/媒体存储
* 或者，将数据库存储用于低流量站点

### 推荐 [!DNL Varnish] 参考体系结构

Magento支持多个全页缓存引擎(文件、Memcache、Redis、 [!DNL Varnish])的开箱即用，并通过扩展扩展扩大了覆盖范围。 [!DNL Varnish] 是推荐的全页缓存引擎。  [!DNL Commerce] 支持多种不同的 [!DNL Varnish] 配置。

对于不要求高可用性的网站，我们建议使用简单的 [!DNL Varnish] 设置Nginx SSL终止。

![简单 [!DNL Varnish] 使用SSL终止进行配置](../assets/performance/images/single-varnish-with-ssl-termination.png)

对于需要高可用性的站点，我们建议使用两层 [!DNL Varnish] 使用SSL终止负载平衡器的配置。

![高可用性两层 [!DNL Varnish] 使用SSL终止负载平衡器的配置](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
