---
title: 企业参考体系结构
description: 了解如何使用Adobe的最新可组合商务技术实施Adobe Commerce。
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Adobe Commerce企业参考架构

Adobe Commerce是一个以体验为导向的平台，它以独一无二的方式在技术灵活性和易用性之间提供了平衡，所有这些都是为了创造卓越的体验来推动业务成果。

Commerce已经过演变，可满足企业对性能、规模和安全性的要求。 采用一种现代化实施方法，该方法会使用Adobe最新的可组合商务解决方案，这对于企业企业的成功至关重要。 本页从技术角度详细描述了现代化的Commerce实施方法。

以下架构图说明了Adobe Commerce与所有Adobe Experience Cloud解决方案之间的数据流。

![显示Adobe Commerce如何连接到Experience Cloud解决方案的架构图](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>图中所示的高级数据流在大多数企业实施中是一致的。 让实施具有唯一性的关键组件是构建目录的方式（特别是对于B2B）。 您应该仔细将目录架构映射到[Commerce Web API](https://developer.adobe.com/commerce/webapi/get-started/)。

## 云基础

云基础架构上的[Adobe Commerce](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/overview)是Commerce实施的基础。 它提供了一个[安全](../../security-and-compliance/shared-responsibility.md)自动托管平台，以及用于在云原生环境中构建、部署、监视和管理Commerce应用程序的自助方法。

请参阅以下Cloud Foundation技术详细信息：

- [**扩展的体系结构**](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) — 自动调整容量以保持稳定、可预测的性能
- [**多个环境**](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) — 预配置了PHP、MySQL (MariaDB)、Redis、RabbitMQ和受支持的搜索引擎技术，以开发、测试和部署您的站点
- [**配置管理**](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/overview) — 可自定义的环境配置文件和命令行界面(CLI)，用于管理应用程序设置、路由、生成和部署操作以及通知。
- [**基于Git的工作流**](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) — 在推送代码更改以进行快速开发和连续部署后自动构建和部署
- [**内置可观察性**](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/monitor/performance) — 可组合来自多个源的日志数据的工具，帮助您管理网站性能和诊断问题
- [**全面的API覆盖**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)和[REST](https://developer.adobe.com/commerce/webapi/rest) API，用于集成核心Commerce应用程序与第三方系统并扩展Commerce功能

## 与Experience Cloud集成

Adobe Commerce与所有Experience Cloud解决方案集成，可大规模提供[个性化商务体验](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu)。

[Data Connection](https://experienceleague.adobe.com/zh-hans/docs/commerce/data-connection/overview)解锁关于购物者购买行为的洞察，以便您能够与其他Adobe数字体验产品跨所有渠道创建个性化的购物体验。

>[!NOTE]
>
>有关更多信息，请参阅以下资源：
>
>- [数字体验Blueprint](https://experienceleague.adobe.com/zh-hans/docs/blueprints-learn/architecture/overview)，了解更多技术详细信息。
>- 请参阅[个性化客户体验](https://experienceleague.adobe.com/zh-hans/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization)。


## 与第三方系统集成

Adobe为开发人员提供了全面的扩展点和工具，用于构建可扩展Commerce核心功能并将Commerce与第三方系统（例如CRM、ERPS和PIMS）集成的应用程序。 这些工具可通过以下方式降低平台的总拥有成本：

- **可扩展性** — 应用程序可以与核心软件分开扩展，以便提高效率和简化升级。
- **隔离** — 隔离环境意味着开发人员可以自行升级或修改其扩展，而无需依赖核心版本。
- **技术独立性** — 开发人员可以选择任何符合其需求的技术栈栈和编码语言。

Adobe提供了以下开发人员工具来构建集成和自定义：

- Adobe Developer App Builder的&#x200B;[**API网格**](https://developer.adobe.com/graphql-mesh-gateway/) — 协调多个API、GraphQL、REST和其他源并将其合并到一个可查询的GraphQL端点中。
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/) — 构建并部署安全且可扩展的Web应用程序，这些应用程序可扩展Commerce功能并与第三方解决方案集成。
- [**事件**](https://developer.adobe.com/commerce/extensibility/events/) — 使用自定义事件触发器与其他可扩展开发工具交互。
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/) — 使用Webhook自动触发Commerce与第三方系统之间的交互。
- [**管理员UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) — 使用商户的新页面和功能自定义并增强Commerce管理员。
- [**集成入门工具包**](https://developer.adobe.com/commerce/extensibility/starter-kit/) — 通过参考集成、入门脚本和标准化架构加速您的Backoffice集成。

>[!NOTE]
>
>请参阅[现代方法：Adobe Commerce中的有效可扩展性](https://experienceleague.adobe.com/zh-hans/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility)。

## 店面服务

Adobe提供一套丰富的智能、可组合的推销服务，帮助您支持关键业务目标。 这些服务还提供了对大规模优化性能至关重要的API。

- [实时搜索](https://experienceleague.adobe.com/zh-hans/docs/commerce/live-search/overview) — 通过此AI支持的搜索工具，为购物者提供更智能、更快速且相关的结果。
- [产品推荐](https://experienceleague.adobe.com/zh-hans/docs/commerce/product-recommendations/overview) — 根据购物者行为、流行趋势、产品相似性等添加AI驱动的推荐。
- [目录服务](https://experienceleague.adobe.com/zh-hans/docs/commerce/catalog-service/guide-overview) — 为客户提供优化的产品体验，同时提高性能、改进可扩展性和提高转化率。
- [支付服务](https://experienceleague.adobe.com/zh-hans/docs/commerce/payment-services/guide-overview) — 通过提供各种支付方式（包括免息分期付款）和单一付款处理、订单和发票视图，提高客户满意度。

## Headless店面

Headless商务是API优先的商务。 Adobe Commerce采用解耦的架构，实现了完全的headless。该架构通过GraphQL API层提供所有Commerce服务和数据。 此架构允许团队独立于核心应用程序开发其前台，从而提供使用新兴技术快速构建和测试新接触点的灵活性。

Adobe提供现代headless storefront技术，它与[Edge Delivery Services](https://www.aem.live/home)提供的优势和功能相同，具有基于文档的创作、性能优先的架构和现成的本机试验。 它利用Adobe Commerce [店面服务](#storefront-services)的规模和性能以及[插入组件](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=zh-Hans)的灵活性和便利性来提供商务功能。

