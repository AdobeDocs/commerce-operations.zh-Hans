---
title: 无外设Adobe Commerce架构
description: 了解Adobe Commerce无头架构方法的独特之处。
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# 无外设Adobe Commerce架构

Adobe Commerce架构的好处是它不是一无是处的建议，商家可以为其业务找到合适的解决方案组合。 他们可以构建基于PWA Studio的PWA，以便获得主要站点体验，或将Adobe Experience Manager用作复杂客户旅程中的层，同时构建自定义前端以试验新的接触点。 没有其他平台能够与Adobe Commerce在其无外设架构上提供的上市时间和灵活性相匹配。

![显示无头Adobe Commerce店面架构的图表](../../../assets/playbooks/headless-storefront-architecture.svg)

每种方法并不互斥。 客户可以构建自己的前端（头部）、使用PWA Studio提供Web/移动体验，和/或使用Adobe Experience Manager来提供玻璃（在完整部署或混合部署中）。

Adobe Commerce始终允许使用REST API进行无头部署。 尽管REST功能强大（尤其是对于批量处理而言），但GraphQL API通过直观的开发人员体验实现了更快的开发速度，允许不影响现有API的更改实现更大的灵活性，并且通过将检索到的数据量减至仅需要的数据量，从而提高性能。

GraphQL是性能API的行业标准，许多顶级电子商务平台都使用该标准。 这是件好事，因为这意味着它是一个经过验证的解决方案，而且市场上有着丰富的专业知识。

虽然Adobe Commerce的店面是耦合的，但商家不必使用Adobe Commerce的传统门面。 商家可以利用Adobe Commerce同类最佳的商务服务来处理后端业务流程，并且使用我们的店面API，集成他们自己的去耦店面以推动前端体验。

现在，让我们看看各种无头选项。

## PWA Studio

第一个是使用PWA Studio构建的渐进式Web应用程序。 部分原因在于PWA是与商务后端分离的无头店面。 借助PWA Studio，商家可以在Adobe Commerce之上构建高性能、可靠且经济实惠的PWA，从而在移动和桌面上提供一流的Web体验。 随着时间的推移，此选项将超过耦合的店面作为默认选项。

大多数商家都明白行业在PWA方面正朝着什么方向发展，许多潜在的拦截器正在迅速拆除。

一周又一周，在PWA Studio领域积累专业技能的合作伙伴数量不断增加，而且我们的客户发布数量也在不断增加。 PWA Studio的最新更新包括可扩展性，这将有助于在与Adobe Commerce Marketplace扩展的兼容性方面取得重大进展。

许多商家可能觉得，他们还没有准备好迎接无头和PWA，因为他们需要严重依赖开发商。 既拥有商务应用程序，又拥有Adobe Commerce开发的主管，其巨大好处之一是它有助于确保跨商务功能的兼容性。

为了使PWA更易于访问并更便于商户管理，我们使业务用户能够使用页面生成器管理日常内容更改、创建新登陆页面等。 这两项强大的功能共同使所有设备和体验都能快速上市。

## Adobe Experience Manager

作为满足您的内容和数字资产管理需求的强大组合，Adobe Experience Manager可帮助商家更快地将以内容为导向的个性化体验推向市场，从而将数字资产管理与机器学习、Adobe Sensei支持的内容和客户历程管理的强大功能相结合。

Adobe Commerce + Adobe Experience Manager是一个强大的故事，因为商务引擎允许企业通过由Adobe Experience Manager提供支持的客户界面启用商务。

## 自定义标题

这里讨论的最后一个选项是构建自定义前端的选项。 此选项适用于拥有现有专业知识的企业以及熟练掌握特定前端堆栈（如React）的内部开发人员。 如果他们不具备Adobe Commerce传统前端开发的技能，他们可以决定构建自己的自定义React前端更具成本效益。

当然，此模型需要强大的客户或系统集成在前端开发技能和资源，并且您无法从与Page Builder等通过PWA Studio获得的内容的本机兼容性中受益。 任何时候，商家在打造一种完全定制的东西，他们都可能失去上市时间的优势。

自定义前端还支持创新和实验。 关于AR/VR或语音商务有很多的讨论，像Adobe Commerce这样的架构让商家能够探索这些选项而不会影响他们现有的网店。
