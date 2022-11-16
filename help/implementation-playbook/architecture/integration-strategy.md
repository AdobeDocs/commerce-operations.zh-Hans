---
title: Adobe Commerce集成策略
description: 查看Adobe Commerce实施的集成策略和选项。
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Adobe Commerce集成策略

集成平台的功能是“不容商量的”。 公司希望从各种接触点访问其电子商务平台，并将其无缝地集成到其技术系统中，特别是其ERP中。 可定制性、全球可扩展性和经济性也在最终平台购买中起着重要作用。

性能优化的GraphQL API、全面的REST API，以及Adobe Commerce与其他系统或服务之间的批量文件导入，均支持店面和后端系统的整体集成方法。

Adobe Commerce GraphQL API提供了全面的店面覆盖，您可以使用这些覆盖与其他店面集成，包括：

- 数字体验平台(DXP)，如Adobe Experience Manager和Bloomreach
- 内容管理系统(CMS)，如Drupal和WordPress
- 现代自定义店面应用程序，如Adobe Commerce、PWA Studio和Vue Storefront

GraphQL提供了高效、特定于渠道的响应，无需过度获取数据，并可灵活部署新的接触点功能。 它还通常选择与销售渠道集成，例如移动设备本机应用程序、POS、IoT、社交渠道以及实时流商务渠道(如Facebook、Google、Instagram、微信和TikTok)。

Adobe Commerce REST API提供全面的系统配置覆盖和数据管理功能，包括产品和目录；购物车、报价和结账；客户、帐户和公司；订单和退货。 REST API支持批量操作、多种身份验证模式和粒度授权，因此通常选择REST API与企业系统集成，包括：

- 企业资源规划(ERP)系统，如SAP
- 产品信息管理(PIM)系统，如Akeneo
- 客户关系管理(CRM)系统，如Salesforce
- 订单管理系统(OMS)，如MOM、Manhattan和SAP
- 仓库管理系统(WMS)或第三方物流(3PL)，如Oracle、 NetSuite和SAP WM
- 配置、价格、报价(CPQ)，如SalesforceCPQ
- 数字资产管理(DAM)，如AdobeDAM。

批量文件导入也被视为集成企业系统（如ERP和PIM）的一个好选项，因为数据不会经常更改，而且您通常通过计划文件导入获得更好的性能。 因此，通常选择批量文件导入来进行每日/每周和每月的完全数据同步，而选择REST API进行增量数据更改同步，以获得更好的性能。 这也只被视为一项计划工作，但可以频繁执行，可能每15分钟到1小时执行一次，具体取决于业务需求。

## 集成选项

Adobe Commerce提供了三个灵活的集成选项：

- 与预建连接器的直接系统到系统集成。 某些系统可能已在Adobe Commerce Marketplace或其自己的网站上拥有Adobe Commerce扩展。

- 通过自定义中间件实现系统到系统的集成。 部署的自定义中间件解决方案将用于处理数据映射、转换和管理。

- 通过iPaaS（集成平台即服务）进行系统到系统的集成，也称为EAI（企业应用程序集成平台），如Mulesoft、Boomi和Software AG。

![Adobe Commerce集成选项](../../assets/playbooks/integration-options.svg)

尽管通常需要实时集成，但在某些情况下也不需要。 Adobe Commerce本地支持 [!DNL RabbitMQ] 作为消息总线启用异步进程，建议对某些不需要实时交换的数据执行此操作，而是使用批处理文件交换或REST批处理数据进程API进行更新以异步处理。
