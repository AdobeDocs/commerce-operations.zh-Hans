---
title: Adobe Commerce集成策略
description: 查看Adobe Commerce实施的集成策略和选项。
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Adobe Commerce集成策略

集成您的平台的能力“不容商量”。 公司希望他们的电子商务平台可以从各种接触点访问，并无缝地集成到他们的技术系统中，特别是他们的ERP。 可定制性、全球可扩展性和经济实惠性在最终购买平台时也扮演着重要角色。

高性能GraphQL API、全面的REST API以及Adobe Commerce与其他系统或服务之间的批量文件导入支持适用于店面和后端系统的整体集成方法。

Adobe Commerce GraphQL API提供了全面的店面覆盖范围，您可以使用它与其他店面集成，包括：

- Adobe Experience Manager和Bloomreach等数字体验平台(DXP)
- Drupal和WordPress等内容管理系统(CMS)
- Adobe Commerce、PWA Studio和Vue Storefront等现代自定义店面应用程序

GraphQL提供了高效、特定于渠道的响应、不会过度获取数据，以及新接触点功能的灵活部署。 它还经常被选为与销售渠道集成，例如本机移动应用程序、POS、物联网、社交渠道以及Facebook、Google、Instagram、微信和TikTok等直播商务渠道。

Adobe Commerce REST API提供全面的系统配置范围和数据管理功能，包括产品和目录；购物车、报价和结账；客户、帐户和公司；以及订单和退货。 REST API支持批量操作、多种身份验证模式和精细授权，因此通常选择REST API与企业系统集成，包括：

- 企业资源规划(ERP)系统，如SAP
- 像Akeneo这样的产品信息管理(PIM)系统
- 客户关系管理(CRM)系统，如Salesforce
- 订单管理系统(OMS)，如MOM、Manhattan和SAP
- 仓库管理系统(WMS)或第三方物流(3PL)，如Oracle、NetSuite和SAP WM
- 配置、定价、报价(CPQ)，如SalesforceCPQ
- 数字资源管理(DAM)，如AdobeDAM。

批处理文件导入也被认为是集成ERP和PIM等企业系统的一个很好的选择，因为此类数据不会经常更改，并且您通常在计划文件导入方面有更好的性能。 因此，通常选择批处理文件导入进行每日/每周和每月完整数据同步，而选择REST API进行增量数据更改同步，以获得更好的性能。 这还仅被视为一项计划工作，但可以根据业务需求经常执行此操作（可能每15分钟到1小时执行一次）。

## 集成选项

Adobe Commerce提供了三个灵活的集成选项：

- 与预建连接器的直接系统到系统集成。 某些系统可能在Adobe Commerce Marketplace或他们自己的网站上已有Adobe Commerce扩展。

- 通过定制中间件实现系统到系统的集成。 所部署的自定义中间件解决方案将用于流程数据映射、翻译和管理。

- 通过iPaaS（Integration Platform-as-a-Service，集成平台 — as-a-Service）进行系统到系统的集成，也称为EAI（企业应用程序集成平台），例如Mulesoft、Boomi和Software AG。

![Adobe Commerce集成选项](../../assets/playbooks/integration-options.svg)

尽管通常需要实时集成，但某些情况下并不一定需要。 Adobe Commerce本机支持 [!DNL RabbitMQ] 作为消息总线启用异步进程，建议对某些不需要实时交换的数据，使用批处理文件交换或REST批处理数据进程API更新以异步处理。
