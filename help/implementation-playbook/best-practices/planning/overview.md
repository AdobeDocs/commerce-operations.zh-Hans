---
title: 实施规划阶段
description: 了解Adobe Commerce项目规划阶段的实施最佳实践。
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# 规划阶段

规划阶段包括以下活动：

- 要求收集
- 建筑设计
- 目录设计
- 项目范围
- 帐户配置
- 用户访问
- 扩展购买

以下各节包括规划阶段的最佳实践信息。

## 要求收集

- **应用程序配置**
   - [配置站点、存储和存储视图（云基础架构）的最佳实践](sites-stores-store-views.md)
   - [如何防止和修复Adobe Commerce站点最常见的五个配置问题](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [缓存最佳实践](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [全页缓存](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache内存大小](opcache-memory-size.md)
   - [报表配置](reporting-configuration.md)

- **数据库配置**
   - [云部署的数据库配置最佳实&#x200B;践](database-on-cloud.md)
   - [MySQL从连接配&#x200B;置](configure-mysql-slave-connection-on-cloud.md)
   - [MySQL触发器用法](mysql-triggers-usage.md)

- **服务配置**
   - [设置Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic — 配置通知渠道](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Redis服务配置的最佳实践&#x200B;](redis-service-configuration.md)
   - [Realpath缓存大小最佳实践](realpath-cache-size.md)

## **建筑设计**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [了解全局参考架构](../../../implementation-playbook/architecture/global-reference.md)

## **目录设计**

以下主题介绍了配置Adobe Commerce目录的性能优化最佳实践，包括建议的类别数、产品有效SKU、产品变体、产品属性和选项等的最大值。

- [类别配置](category-limits.md)
- [产品配&#x200B;置](product-sku-limits.md)
- [产品变量配置](product-variations.md)
- [产品选项配置](product-options.md)
- [产品属性配&#x200B;置](product-attributes-and-options.md)
- [产品列表的分页配置](product-listing-pagination.md)

## **销售和营销**

- [产品车限制的最佳实践&#x200B;](product-cart.md)
- [配置促销活动的最佳实践](product-cart-promotions.md)

## **项目范围**

- [合作伙伴升级](partner-escalation.md)

## **购买扩展**

- [在Adobe Commerce中使用第三方扩展的最佳实&#x200B;践](extensions.md)
