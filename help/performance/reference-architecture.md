---
title: 参考架构
description: 查看Adobe Commerce部署中推荐的参考架构的示意图。
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# 参考架构

本主题介绍了一般性建议设置，适用于Adobe Commerce实例，这些实例使用在数据中心（非虚拟化）物理托管的普通服务器，其中资源不与其他用户共享。 您的托管提供商(尤其是专门从事Commerce高性能托管业务的提供商)可能会建议您采用对您的要求同样有效或更加有效的其他设置。

有关云基础架构环境上的Adobe Commerce，请参阅[入门架构](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/architecture/starter-architecture)。

## [!DNL Commerce]参考体系结构图

[!DNL Commerce]参考架构图表示设置可缩放[!DNL Commerce]站点的最佳实践方法。

图中每个元素的颜色指示该元素是Magento Open Source还是Adobe Commerce的一部分，以及是否必需。

* Magento Open Source需要橙色元素
* 灰色元素对于Magento Open Source是可选的
* 蓝色元素是Adobe Commerce的可选元素

![Commerce参考架构图](../assets/performance/images/ref-architecture-2.3.png)

以下部分提供了有关Commerce参考架构图每个部分的建议和注意事项。

### [!DNL Varnish]

* [!DNL Varnish]群集可以扩展到站点的流量
* 根据所需的缓存页数优化实例大小
* 在高流量站点上，使用[!DNL Varnish]主机以确保在缓存中刷新每个Web层（最多）一个请求

### Web

* 为流量和冗余启用节点扩展
* 一个节点是主节点并运行cron
* 或者，使用专用的管理员和工作节点

### 缓存

* 考虑为会话实施单独的Redis实例
* 每个缓存可以有一个Redis实例
* 调整实例大小以包含预期的最大缓存大小

### 数据库和队列

* 高流量站点可以使用从属数据库调整数据库性能，并为订单/购物车拆分数据库(在Adobe Commerce中)
* 考虑使用从数据库实现快速恢复并用于数据备份
* 低流量网站可以将图像存储在数据库中

### Search {#search-heading}

* 根据搜索流量调整实例数

### 存储

* 考虑将GFS或GlusterFS用于pub/media存储
* 或者，将数据库存储用于低流量站点

### 推荐的[!DNL Varnish]参考体系结构

Magento支持多个开箱即用的全页缓存引擎(File、Memcache、Redis、[!DNL Varnish])，并通过扩展扩展扩展了覆盖范围。 [!DNL Varnish]是推荐的完整页面缓存引擎。  [!DNL Commerce]支持许多不同的[!DNL Varnish]配置。

对于不需要高可用性的网站，我们建议使用带有Nginx SSL终止的简单[!DNL Varnish]设置。

包含SSL终止的![简单[!DNL Varnish]配置](../assets/performance/images/single-varnish-with-ssl-termination.png)

对于需要高可用性的网站，我们建议使用带有SSL终止负载平衡器的两层[!DNL Varnish]配置。

使用SSL终止负载平衡器的![高可用性两层[!DNL Varnish]配置](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
