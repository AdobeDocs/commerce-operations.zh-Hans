---
title: Adobe Commerce集成选项
description: 探索用于将其他系统与Adobe Commerce实施集成的选项。
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 典型集成点和数据流

集成和数据流有两种主要方法，这两种方法非常相似，但有一个关键区别。

## 整体式

下图描述了一种将Adobe Commerce用作后端系统和店面应用程序的整体方法：

![Adobe Commerce整体图](../../assets/playbooks/integration-monolith.svg)

## Headless

下图描述了一种使用Adobe Commerce作为后端系统，与DXP/CMS/自定义应用程序集成作为店面应用程序的Headless方法：

![Adobe Commerce headless图](../../assets/playbooks/integration-headless.svg)

整体式和Headless式方法的唯一区别是店面集成，这影响了客户的用户体验。 Monolithic直接使用Adobe Commerce店面与第三方服务集成，而Headless则依靠其自己的店面来自定义并与相同的服务集成。 某些服务(如支付和单点登录(SSO))需要同时自定义店面和Adobe Commerce才能最终确定集成流程。

## 第三方系统

一些常用服务已有出色的扩展可支持Adobe Commerce或常用店面解决方案，例如PWA Studio、Adobe Experience Manager和Vue Storefront，可从其扩展市场或相关的第三方网站中找到这些解决方案。 即使不存在现有扩展，在Adobe Commerce和其他Headless商店之间实施集成的工作也类似。 所有第三方服务通常都有用于解释如何与它们集成的文档。 这些服务只是一些例子；不同的国家和市场可能有不同的选择。

## 企业集成

对于企业系统集成（通常也称为后端集成），会对业务数据流产生影响。 根据不同的业务类型和需求，可以采用我们已经介绍的三种不同的集成选项。

SKU、库存和基本价格等产品必备数据通常来自ERP，而销售价格通常由每个销售渠道(例如Adobe Commerce)或CPQ（B2B或私人销售）管理。 由于产品必备数据（库存除外）不会经常更改，因此最佳实践是通过REST API或批量文件导入使用计划的批量更新。 对于库存，最佳做法是每天对与不同销售渠道共享的产品库存进行全面更新，以避免过度销售。 此外，还计划在24小时内对ERP进行增量更改。

产品目录、元数据和营销内容可以由每个销售渠道(例如Adobe Commerce)单独管理，也可以从集中PIM进行管理。 由于也不会经常更改元数据，因此最佳实践是通过REST API或批量文件导入使用计划的批量更新。

订单数据包括订单、报价(B2B)、装运、退货和交换数据，通常由集中式OMS和WMS系统管理。 订单数据应尽快同步，因此REST API通常是最佳选择。 为了获得更好的性能，请考虑减少API调用的数量。 对于订单状态、发运、退货和交换数据，请考虑计划REST批量更新API（以小时或分钟为单位）。

B2B数据通常通过集中式CRM进行管理。 实时API用于验证现有客户和创建新客户。 对于B2B，可能需要引入更多API，以便在Adobe Commerce与您的CRM或CPQ之间同步不同的公司员工、组和价目表。

还有一些其他的系统集成，如用于电子邮件营销的eDM和用于业务数据分析的商业智能，这些集成通常通过REST API或文件导出/导入来完成，这通常受现有扩展的支持。
