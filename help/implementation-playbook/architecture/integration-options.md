---
title: Adobe Commerce集成选项
description: 探索将其他系统与Adobe Commerce实施集成的选项。
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 典型的集成点和数据流

集成和数据流有两种主要方法，它们非常相似，但有一个关键区别。

## 整体

下图描述了一种使用Adobe Commerce作为后端系统和店面应用程序的整体方法：

![Adobe Commerce单石图](../../assets/playbooks/integration-monolith.svg)

## 无头

下图描述了一种无头方法，该方法使用Adobe Commerce作为与DXP/CMS/自定义应用程序集成的后端系统作为店面应用程序：

![Adobe Commerce无头图](../../assets/playbooks/integration-headless.svg)

整体式和无头式方法的唯一区别在于前端集成，这会影响客户的用户体验。 单块式直接使用Adobe Commerce店面与第三方服务相集成，而无头式店面则依赖其自己的店面来定制和集成同一服务。 一些服务(如支付和单点登录(SSO))需要店面和Adobe Commerce自定义功能才能最终确定集成流程。

## 第三方系统

一些热门服务已经拥有了非常好的扩展功能来支持Adobe Commerce或热门的店面解决方案，例如PWA Studio、Adobe Experience Manager和Vue Storefront，这些解决方案可从其扩展市场或相关的第三方网站中找到。 即使没有现有的扩展，在实施Adobe Commerce与其他无头店之间的集成方面也是类似的。 所有第三方服务通常都有文档来解释如何与它们集成。 这些服务只是一些例子；不同国家和市场可能有不同的选择。

## 企业集成

对于企业系统集成（通常也称为后端集成），会对业务数据流产生影响。 根据不同的业务类型和需求，它可以使用我们已经引入的三种不同的集成选项。

SKU、库存和基本价格等产品必需数据通常来自ERP，而销售价格通常由每个销售渠道(例如Adobe Commerce)或CPQ（B2B或私人销售）来管理。 由于产品必需数据（库存除外）不会经常更改，因此最佳实践是通过REST API或批量文件导入来使用计划的批量更新。 对于库存，最佳做法是每天对与不同销售渠道共享的产品库存进行全面更新，以避免过度销售。 此外，还计划在24小时内对ERP中的增量更改进行计划。

产品目录、元数据和营销内容可由每个销售渠道(例如，Adobe Commerce)或中央PIM单独管理。 由于元数据也不会频繁更改，因此最佳实践是通过REST API或批量文件导入来使用计划的批量更新。

订单数据包括订单、报价(B2B)、发运、退货和交换数据，这些数据通常通过集中的OMS和WMS系统进行管理。 订单数据应尽快同步，因此REST API通常是最佳选项。 为了提高性能，请考虑减少API调用的数量。 对于订单状态、发运、退货和交换数据，请考虑在小时或分钟内计划REST批量更新API。

B2B数据通常通过集中式CRM进行管理。 实时API用于验证现有客户和创建新客户。 对于B2B，可能需要引入更多API，以便在Adobe Commerce与您的CRM或CPQ之间同步不同的公司员工、组和价目表。

还有其他一些系统集成，例如用于电子邮件营销的eDM和用于业务数据分析的业务智能，这些集成通常通过REST API或文件导出/导入（通常由现有扩展支持）来完成。
