---
title: 实施规划阶段
description: 了解Adobe Commerce项目规划阶段的实施最佳实践。
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 1%

---

# 规划阶段

规划阶段包括以下活动：

- 建筑设计
- 目录设计
- 扩展购买
- 项目范围
- 要求收集
- 销售和营销

以下部分包含规划阶段的最佳实践信息。

## 要求收集

<table>
<thead>
  <tr>
    <th>最佳实践</th>
    <th>描述</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>应用程序配置</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">配置站点、商店和商店视图</a></td>
    <td>配置站点、商店和存储视图以最大限度地提高站点性能。</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">常见配置问题</a></td>
    <td>修复和防止Adobe Commerce站点最常见的五个配置问题。</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">缓存</a></td>
    <td>使用缓存管理工具提高站点的性能。</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">全页缓存</a></td>
    <td>了解在Adobe Commerce或Magento Open Source扩展中实施缓存时如何使用公共数据。</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">OPcache内存大小</a></td>
    <td>通过OPcache内存消耗的特定设置，避免性能下降。</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">配置报表</a></td>
    <td>如果不使用报表模块，请通过删除报表模块来优化网站性能。</td>
  </tr>
  <tr>
    <td colspan="2"><em>数据库配置</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">为云部署配置数据库</a></td>
    <td>配置数据库和应用程序设置，以在云基础架构项目上部署Adobe Commerce时提高性能。</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">配置MySQL</a></td>
    <td>了解MySQL触发器和从属连接如何影响站点性能以及如何有效使用它们。</td>
  </tr>
  <tr>
    <td colspan="2"><em>服务配置</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">设置Fastly</a></td>
    <td>在云基础架构项目中为Adobe Commerce配置Fastly服务。</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">为New Relic配置通知渠道</a></td>
    <td>访问您的New Relic功能板并分析来自Adobe Commerce的云基础架构项目数据。</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">配置Redis</a></td>
    <td>通过为Adobe Commerce使用扩展的Redis缓存实现来提高缓存性能。</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Realpath缓存大小</a></td>
    <td>通过更新PHP 'readlpath'缓存配置以使用推荐的设置来优化性能。</td>
  </tr>
</tbody>
</table>

## 建筑设计

| 最佳实践 | 描述 |
|----------------------------------------------------------------------------------------|----------------------------------------------------------|
| [全球参考体系结构(GRA)](../../architecture/global-reference/examples.md) | 了解组织GRA代码库的常用方法。 |

## 目录设计

| 最佳实践 | 描述 |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [类别配置](catalog-management.md#category-limits) | 配置产品类别以获得最佳性能。 |
| [产品配置&#x200B;](catalog-management.md#product-sku-limits) | 配置产品SKU以获得最佳性能。 |
| [产品变体配置](catalog-management.md#product-variations) | 配置产品变体以获得最佳性能。 |
| [产品选项配置](catalog-management.md#product-options) | 配置产品选项以获得最佳性能。 |
| [产品属性配置&#x200B;。](catalog-management.md#product-attributes) | 配置产品属性以获得最佳性能。 |
| [产品列表的分页配置](catalog-management.md#product-listing-pagination) | 配置产品列表分页以获得最佳性能。 |

## 扩展

| 最佳实践 | 描述 |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [在Adobe Commerce中使用第三方扩展](extensions.md) | 了解如何避免由第三方Adobe Commerce扩展引起的性能问题。 |

## 项目范围

| 最佳实践 | 描述 |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [合作伙伴升级](partner-escalation.md) | 准备向Adobe客户团队上报合作伙伴问题，或了解如何避免升级。 |
| [支付存储处理](payment-processing-storage.md) | 安全地处理和存储付款详细信息。 |

## 销售和营销

| 最佳实践 | 描述 |
|------------------------------------------------------------|--------------------------------------------------------------|
| [产品购物车限制](catalog-management.md#cart-limits) | 管理购物车限制以获得最佳性能。 |
| [配置促销活动](catalog-management.md#promotions) | 为购物车中的商品配置销售和促销活动。 |
