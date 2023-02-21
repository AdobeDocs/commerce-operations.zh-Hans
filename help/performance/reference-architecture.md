---
title: 参考架构
description: 查看推荐的Adobe Commerce参考架构和Magento Open Source部署的图表。
source-git-commit: 065c56f20ba5b1eef8c331c5c2f5649902f1442b
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# 参考架构

本主题介绍一个通用的推荐设置，用于使用物理托管在数据中心（非虚拟化）中且资源未与其他用户共享的普通服务器的Adobe Commerce和Magento Open Source实例。 您的托管提供商（尤其是如果它专门从事商务高性能托管）可能会建议使用其他设置，以便对您的要求同样或更有效。

有关云基础架构环境中的Adobe Commerce，请参阅 [入门架构](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] 参考架构图

的 [!DNL Commerce] 参考架构图代表了设置可扩展的最佳实践方法 [!DNL Commerce] 网站。

图中每个元素的颜色指示该元素是Magento Open Source的一部分还是Adobe Commerce的一部分，以及是否需要。

* 橙色元素是Magento Open Source所必需的
* 灰色元素是可选的Magento Open Source
* 蓝色元素是Adobe Commerce的可选元素

![商务参考架构图](../assets/performance/images/ref-architecture-2.3.png)

以下各节为商务参考架构图的每个部分提供了建议和注意事项。

### [!DNL Varnish]

* A [!DNL Varnish] 群集可以按站点流量进行扩展
* 根据所需的缓存页数调整实例大小
* 在高流量网站上，使用 [!DNL Varnish] 主控，以确保在缓存上刷新每个Web层一个请求（最多）

### Web

* 为流量和冗余启用节点规模
* 一个节点主控，并运行cron
* 或者，使用专用的管理员和工作人员节点

### 缓存

* 考虑为会话实施单独的Redis实例
* 每个缓存可以有一个Redis实例
* 调整实例大小以包含最大的预期缓存大小

### 数据库和队列

* 高流量站点可以使用从数据库调节数据库性能，并为订单/购物车拆分数据库(在Adobe Commerce中)
* 考虑使用从数据库来实现快速恢复和数据备份
* 低流量站点可以在数据库中存储图像

### 搜索 {#search-heading}

* 根据搜索流量调整实例数

### 存储

* 考虑使用GFS或GlusterFS进行发布/媒体存储
* 或者，将数据库存储用于低流量站点

### 建议 [!DNL Varnish] 参考架构

Magento支持多个全页缓存引擎(文件、内存缓存、Redis、 [!DNL Varnish])开箱即用，以及通过扩展扩展扩展的覆盖范围。 [!DNL Varnish] 是建议的全页缓存引擎。  [!DNL Commerce] 支持多种不同 [!DNL Varnish] 配置。

对于不需要高可用性的站点，我们建议使用简单的 [!DNL Varnish] 设置，并终止Nginx SSL。

![简单 [!DNL Varnish] 使用SSL终止进行配置](../assets/performance/images/single-varnish-with-ssl-termination.png)

对于需要高可用性的站点，我们建议使用2层 [!DNL Varnish] 使用SSL终止负载平衡器进行配置。

![高可用性两层 [!DNL Varnish] 使用SSL终止负载平衡器进行配置](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
