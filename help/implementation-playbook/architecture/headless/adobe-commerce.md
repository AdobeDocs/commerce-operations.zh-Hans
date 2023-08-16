---
title: Headless Adobe Commerce架构
description: 了解是什么使得Adobe Commerce的Headless架构方法独树一帜。
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Headless Adobe Commerce架构

Adobe Commerce架构的好处在于，它不是全有或全无的命题，商家可以为他们的业务找到正确的解决方案组合。 他们可以为其主要站点体验构建PWA Studio支持的PWA，或者在复杂的客户历程中使用Adobe Experience Manager作为层，同时构建自定义前端以试验新的接触点。 其他任何平台都无法与Adobe Commerce的Headless架构相媲美上市时间和灵活性。

![显示Headless Adobe Commerce店面架构的示意图](../../../assets/playbooks/headless-storefront-architecture.svg)

每种方法并不互相排斥。 客户可以构建自己的前端(head)，将PWA Studio用于Web/移动体验，和/或将Adobe Experience Manager用于玻璃（在完全部署或混合部署中）。

Adobe Commerce始终允许使用REST API进行Headless部署。 虽然REST非常强大（尤其是对于批量处理），但是对于Headless而言，GraphQL API通过直观的开发人员体验实现了更快的开发，通过允许不影响现有API的更改而提高了灵活性，并且通过最大限度地减少检索到恰好所需的数据量而提高了性能。

GraphQL是性能API的行业标准，许多顶级电子商务平台都使用该标准。 这是一件好事，因为这意味着这是一个经验证的解决方案，而且市场上存在这方面的专业知识。

虽然Adobe Commerce确实提供了一个合并的店面作为选项，但商家无需使用Adobe Commerce旧版店面。 商家可以利用Adobe Commerce同类最佳的商务服务来处理后端业务流程，并使用我们的店面API集成他们自己的分离式店面以提高前端体验。

现在，让我们看一下各种Headless选项。

## PWA Studio

第一个是使用PWA Studio构建的渐进式Web应用程序。 部分原因在于一个PWA是与Commerce后端分离的Headless店面。 借助PWA Studio，商家可以在Adobe Commerce之上构建高性能、可靠且经济高效的PWA，从而在移动和桌面上提供一流的Web体验。 随着时间的推移，这将取代耦合的店面作为默认选项。

大多数商家都明白该行业在PWA方面的发展方向，许多潜在的阻断因素正迅速被移除。

一周又一周，在PWA Studio方面积累专业知识的合作伙伴数量不断增长，而我们推出客户的数量也在不断增长。 PWA Studio的最新更新包括可扩展性，将有助于在与Adobe Commerce Marketplace扩展兼容方面取得显着进展。

许多商家可能会觉得他们还没有准备好迎接无头和PWA，因为他们需要严重依赖开发商。 让Adobe Commerce开发的商务应用程序和Head具有的巨大优势之一是，它有助于确保各种商务功能之间的兼容性。

为了让我们的商家更易于访问和管理PWA，我们授权业务用户使用Page Builder管理日常内容更改、创建新登陆页面等。 这两项强大的功能结合在一起，可加快在所有设备和体验中进行营销的速度。

## Adobe Experience Manager

Adobe Experience Manager是满足您的内容和数字资产管理需求的强大组合，可帮助商家更快地将内容导向的个性化体验推向市场，同时将数字资产管理与机器学习、Adobe Sensei支持的内容和客户历程管理的强大功能结合起来。

Adobe Commerce加Adobe Experience Manager就是一个强有力的例子，商业引擎允许企业通过由Adobe Experience Manager提供支持的客户界面来启用商业。

## 自定义标头

此处讨论的最后一个选项是构建自定义前端选项。 此选项适用于拥有现有专业知识的企业和内部开发人员，他们擅长特定前端栈栈，如React。 如果他们没有Adobe Commerce传统前端开发方面的技能，他们可以认定构建自己的自定义React前端更经济高效。

自然，此模型需要强大的客户或系统集成才能前端开发技能和资源，并且您无法获得与Page Builder等内容的原生兼容性好处(通过PWA Studio即可获得)。 每当商家打造完全定制的产品时，他们可能会失去上市时间的优势。

自定义前端还支持创新和实验。 关于AR/VR或语音商务，有很多讨论，而像Adobe Commerce这样的架构允许商家探索这些选项，而不影响他们现有的网络商店。
