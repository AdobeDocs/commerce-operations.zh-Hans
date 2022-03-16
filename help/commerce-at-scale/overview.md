---
title: 大规模交付体验
description: 了解如何使用Adobe Commerce和Adobe Experience Manager大规模提供体验。
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
debug: true
source-git-commit: 442bb3f2c448de2ed70a3033d399025cc39e8744
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 使用Adobe Commerce、商务集成框架和Adobe Experience Manager大规模提供体验

在AEM和Adobe Commerce之间使用CIF作为连接器的一种推荐集成模式是，AEM拥有表示层（“玻璃”），而Adobe Commerce则将商务后端作为“无头”后端提供支持。 此集成方法利用了每个应用程序的优势：AEM的创作、个性化和全渠道功能，以及Adobe Commerce的电子商务操作。

在AEM/CIF/Adobe Commerce环境中，电子商务网站访客最初将到达AEM。 AEM将检查其调度程序缓存中是否有可用的请求页面。 如果页面存在，则会向访客提供该缓存页面，而无需进一步处理。 如果调度程序不包含请求的页面，或者该页面已过期，则调度程序会请求AEM发布程序生成页面，发布程序会根据需要调用Adobe Commerce以获取电子商务数据来构建页面。 随后，构建的页面将传递到调度程序以提供给访客，并进行缓存，以防止在其他访客对同一页面发出后续请求时，将进一步加载到服务器上。

![AdobeExperience Manager和Adobe Commerce架构概述图](../assets/commerce-at-scale/overview.png)

服务器端渲染和客户端渲染的组合可用于AEM/CIF/Adobe Commerce模型：服务器端渲染以交付静态内容，客户端渲染以通过从用户浏览器中直接为特定组件调用Adobe Commerce来交付频繁更改的或个人的动态内容。

有关AEM电子商务店面示例的产品详细信息页面中不同组件的示例，请参见以下示例：

![AdobeExperience Manager和Adobe Commerce架构概述图](../assets/commerce-at-scale/product-details-page.svg)

## 服务器端渲染

电子商务页面(如产品详细信息页面(PDP)和产品列表页面(PLP))不太可能频繁更改，并且适合在使用AEM CIF核心组件在服务器端渲染后完全缓存。 应使用在AEM中创建的通用模板在AEM发布器上呈现页面。 这些组件通过GraphQL API从Adobe Commerce获取数据。 这些页面是动态创建的，呈现在服务器上，缓存在AEM调度程序中，然后交付到浏览器。 上述示例的紫色框中显示了这些示例。

## 客户端渲染

当显示更多动态属性（如库存水平/可用性或价格）时，例如在产品详细信息页面(PDP)上，可以使用客户端组件。 虽然可以使用上述服务器端渲染方法在调度程序上构建和缓存模板页面，但在静态页面本身中，可以有动态客户端Web组件。 这些动态组件可以通过GraphQL API直接在客户端的浏览器中通过Adobe Commerce获取数据，例如，在PDP上实时检查当前价格或库存水平。 这可确保在页面加载时始终获取通常对实时显示至关重要的内容。 以上示例的红色框中显示了这些示例。

在结帐过程中，还可以使用AEM模板和客户端渲染的组合：客户端购物车组件呈现购物车、结帐表单以及与支付服务提供商的集成。 此混合方法还可用于Adobe Commerce的帐户管理功能，如创建帐户、登录帐户和忘记密码。
