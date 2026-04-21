---
title: 修补程序发布计划
description: 了解 Adobe 计划何时发布 Adobe Commerce 的新补丁和安全修复。
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 0f46bdfd0afbca07e0d60e995ee9426f5408671d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 4%

---


# 修补程序发布计划

Adobe不断努力在使产品升级变得简单且可预测，同时更快地为早期采用者提供改进之间找到合适的平衡（请参阅[版本控制策略](versioning-policy.md)）。

此时间表的目的是提供Adobe计划何时宣布核心Adobe Commerce PHP应用程序的每个受支持发行行的[修补程序](versioning-policy.md#patch-release)的发布日期。 修补程序版本提供了升级核心代码库的机会，可确保您的平台安全、可靠且高性能。

>[!NOTE]
>
>要了解有关新功能、云基础架构和可扩展性版本的更多信息，请参阅[Adobe Commerce Services](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all)版本文档。

除了此页面上列出的计划质量、安全性和测试版修补程序之外，Adobe还通过[质量修补程序工具](versioning-policy.md#individual-patch)提供对[单个修补程序](../tools/quality-patches-tool/usage.md)的访问。 该工具允许您应用、还原和查看有关已安装Adobe Commerce版本可用的所有单个修补程序的一般信息。

Adobe Commerce补丁发行版本基于以下准则发布：

- **独立的安全修补程序文件** — 单独发布非累积的[安全修补程序文件](versioning-policy.md#isolated-security-patch-file)以实现更快的修正，并将其合并到下一个完整的安全修补程序中。 要应用独立的安全修补程序文件，客户必须在其受支持的版本行上使用最新的仅安全修补程序发行版（最新的 — p版本），因为独立的安全修补程序将专门针对该版本进行测试。

- **安全修补程序** — 至少每年为所有[受支持](versioning-policy.md#security-patch-release)发行行发布[个安全修补程序](lifecycle-policy.md)。 这些修补程序包括所有以前发布的安全性、合规性和质量修补程序。  如有必要，Adobe可能会发布其他安全修补程序，但不保证一定会发布。

- **Patch** — 每年（5月）发布适用于Adobe Commerce 2.4.x LTS版本行的完整[修补程序](versioning-policy.md#patch-release)（3年支持期）。

- **Alpha修补程序** — 每年发布一个Adobe Commerce 2.4.x LTS发行行的[Alpha修补程序](versioning-policy.md#alpha-patch-release)。

- **Beta修补程序** — 每年发布一个Adobe Commerce 2.4.x LTS发行行的[Beta修补程序](versioning-policy.md#beta-patch-release)。

有关详细信息，请参阅以下图像：

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![2026 Adobe Commerce版本日历](../assets/release/release-calendar.png)


## 发布通知渠道

Adobe通过以下渠道通知客户新的修补程序版本：

- [Adobe安全公告与建议](https://helpx.adobe.com/security/security-bulletin.html#magento)
- 电子邮件
- 产品内警报

>[!NOTE]
>
> 有关每个次要、补丁和安全版本的发行日期以及常规支持结束日期，请参阅[已发行版本](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions)。
