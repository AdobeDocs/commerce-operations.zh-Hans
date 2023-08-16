---
title: Adobe Commerce全球参考架构
description: 通过利用全球参考架构，充分利用您的Adobe Commerce实施。
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
feature: Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# 全球参考体系结构(GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

当企业在多个本地市场（使用本地化的货币、语言、媒体、共享目录和独特购物车）上经营多个网站，并且希望避免实施相同功能和集成所花费的不必要成本时，全球参考体系结构(GRA)始终是一个不错的选择。

![说明体系结构差异成本的表](../../assets/playbooks/divergent-architecture.svg)

![说明在体系结构中整合的成本的表](../../assets/playbooks/consolidated-architecture.svg)

GRA为：

- 实施方法
- 部署策略
- 流程治理模型

GRA不是：

- 产品“功能”
- 对于任何Commerce平台都是唯一的
- 仅适用于全球业务用例

GRA影响：

- 如何交付代码

   - 围绕特定于用途的代码存储库构建，这些存储库可提供不同的体验。

- 如何集成业务系统

   - 按品牌和/或地区整合与业务系统的连接。

- 如何开发和维护自定义

   - 确保自定义集中且特定于域，以便所有自定义工作都是从业务的整体角度进行的。

- 如何启用新市场

   - 简化了多个渠道和市场的发布，否则，这些渠道和市场将花费大量时间和金钱。
