---
title: 耦合式店面架构
description: 了解无头Adobe Commerce体系结构的上下文中，耦合的店面意味着什么。
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# 耦合（旧版）Adobe Commerce店面架构

大多数商业客户当前的默认部署选项包括：

- 跨B2B和B2C的100%功能支持
- 成熟的参考主题(Luma)，可快速部署/自定义
- 成熟的SI合作伙伴实施专业知识
- 与页面生成器或暂存和预览等商务功能完全兼容
- 与Adobe Commerce Marketplace中的扩展具有广泛的兼容性

![显示耦合的Adobe Commerce店面架构的图表](../../../assets/playbooks/coupled-storefront-architecture.svg)

## 旧式店面的缺点

- **非无头** — 整个Adobe Commerce应用程序的所有部分。 前端和后端之间的业务逻辑和流程不分离。

- **非PWA** — 尽管主题是响应式的，但站点性能远远落后于同类最佳PWA。

- **前端架构(Adobe Commerce UI组件)**—Adobe Commerce/PHP专家将在旧式店面上构建。

在开始使用无头选项之前，我们先从更熟悉的店面架构开始。 如果无头是相互分离的，则这将是耦合的店面架构，最常见于我们的Luma演示。

在这里，店面功能与核心商务服务紧密集成，而不是由该GraphQL API层分隔。 所以，在这个主题中，有很多商业逻辑。 这种方法不是无头的，也不是PWA。

这是当前最常用的选项，因为商户在B2B和B2C商务功能上都百分之百支持该功能。 该社区熟悉它，周围有一个成熟的专业生态系统，并且与Adobe Commerce Marketplace扩展具有广泛的兼容性。

但是，它没有我们早些时候谈到的好处。 如果不分层，则在进行更改时会存在许多依赖项和潜在的故障点。 它的表现不如实施得当的PWA，如果商家在Adobe Commerce或PHP开发方面没有专业知识，他们就必须去寻找这些资源。
