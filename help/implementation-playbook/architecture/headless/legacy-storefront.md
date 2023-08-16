---
title: 耦合店面体系结构
description: 了解在Headless Adobe Commerce架构中，耦合店面意味着什么。
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# 耦合（旧版）Adobe Commerce店面架构

大多数商业客户当前的默认部署选项包括：

- 跨B2B和B2C 100%功能支持
- 可快速部署/自定义的成熟参考主题(Luma)
- 成熟的SI合作伙伴实施专业知识
- 与商业功能（如页面生成器或暂存和预览）完全兼容
- 与Adobe Commerce Marketplace中的扩展广泛兼容

![显示耦合的Adobe Commerce店面架构的示意图](../../../assets/playbooks/coupled-storefront-architecture.svg)

## 旧店面的缺点

- **不是Headless** — 整体式Adobe Commerce应用程序的所有部分。 前端和后端之间没有业务逻辑和流程分离。

- **不PWA** — 尽管主题响应式很强，但站点性能远远落后于同类最佳PWA。

- **前端架构(Adobe Commerce UI组件)**—Adobe Commerce/PHP专家，在旧式店面的基础上进行构建。

在介绍Headless选项之前，让我们先从更熟悉的店面架构开始。 如果Headless是分离的，则这将是耦合的店面架构，最常见的是Luma演示。

这是店面功能与核心商务服务紧密集成的地方，而不是由该GraphQL API层分隔开。 因此，有很多业务逻辑与这个主题相耦合。 这种方法不是headless，也不是PWA。

这是目前商家最常使用的选项，因为它对B2B和B2C Commerce功能具有100%的功能支持。 社区对此非常熟悉，围绕IT有一个成熟的专业生态系统，并且与Adobe Commerce Marketplace扩展具有广泛的兼容性。

然而，它缺乏我们之前谈到的好处。 如果不分离层，进行更改时会有许多依赖关系和潜在的故障点。 它不像一个实施良好的PWA那样性能优异，如果商家不具备Adobe Commerce或PHP开发方面的专业知识，他们将不得不去寻找那些资源。
