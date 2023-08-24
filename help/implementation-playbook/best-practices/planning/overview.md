---
title: 实施规划阶段
description: 了解Adobe Commerce项目规划阶段的实施最佳实践。
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 规划阶段

规划阶段包括以下活动：

- 要求收集
- 建筑设计
- 目录设计
- 项目范围
- 帐户设置
- 用户访问权限
- 扩展购买

以下部分包含规划阶段的最佳实践信息。

## 要求收集

- **应用程序配置**
   - [配置站点、商店和存储视图的最佳实践（云基础架构）](sites-stores-store-views.md)
   - [如何防止和修复Adobe Commerce Sites最常见的五个配置问题](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [缓存最佳实践](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [全页缓存](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache内存大小](opcache-memory-size.md)
   - [报告配置](reporting-configuration.md)

- **数据库配置**
   - [适用于云部署的数据库配置最佳实践&#x200B;。](database-on-cloud.md)
   - [MySQL配置&#x200B;](mysql-configuration.md)

- **服务配置**
   - [设置Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic — 配置通知渠道](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Redis服务配置的最佳实践&#x200B;。](redis-service-configuration.md)
   - [Realpath缓存大小最佳实践](realpath-cache-size.md)

## **建筑设计**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [了解全球参考体系结构](../../../implementation-playbook/architecture/global-reference.md)

## **目录设计**

以下主题描述了配置Adobe Commerce目录的性能优化最佳实践，包括类别数、产品有效SKU、产品变体、产品属性和选项等的建议最大值。

- [类别配置](catalog-management.md#category-limits)
- [产品配置&#x200B;](catalog-management.md#product-sku-limits)
- [产品变体配置](catalog-management.md#product-variations)
- [产品选项配置](catalog-management.md#product-options)
- [产品属性配置&#x200B;。](catalog-management.md#product-attributes)
- [产品列表的分页配置](catalog-management.md#product-listing-pagination)

## **销售和营销**

- [有关产品购物车限制的最佳实践](catalog-management.md#cart-limits)
- [配置促销活动的最佳实践](catalog-management.md#promotions)

## **项目范围**

- [合作伙伴升级](partner-escalation.md)
- [支付存储处理](payment-processing-storage.md)

## **购买扩展**

- [在Adobe Commerce中使用第三方扩展的最佳实践](extensions.md)
