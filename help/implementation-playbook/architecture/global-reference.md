---
title: Adobe Commerce全局参考架构
description: 利用全局参考架构，充分利用您的Adobe Commerce实施。
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# 全局参考架构(GRA)

在多个本地市场中运行具有多个品牌网站（具有本地化的货币、语言、媒体、共享目录和独特购物车）的企业，以及希望避免实施相同功能和集成的不必要成本的企业时，全球参考架构(GRA)始终是一个不错的选择。

![解释建筑差异的成本表](../../assets/playbooks/divergent-architecture.svg)

![说明在架构中整合成本的表](../../assets/playbooks/consolidated-architecture.svg)

GRA是：

- 实施方法
- 部署策略
- 流程管理模型

GRA不是：

- 产品“功能”
- 任何商务平台均独有
- 仅适用于全球业务用例

GRA影响：

- 代码交付方式

   - 围绕特定于用途的代码存储库构建，这些存储库可提供不同的体验。

- 如何集成业务系统

   - 按品牌和/或地区整合与业务系统的连接。

- 如何开发和维护定制

   - 确保自定义是集中的并特定于域的，以便从整体角度为业务完成所有自定义工作。

- 如何启用新市场

   - 简化了多个渠道和市场的发布，否则，这些渠道和市场将花费大量的时间和资金。
