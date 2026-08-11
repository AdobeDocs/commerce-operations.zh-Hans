---
title: '[!DNL Commerce Version Tool]发行说明'
description: 了解 [!DNL Commerce Version Tool] 版本，包括新的修补程序状态报告、CVE保护状态、CSV输出和缓存行为。
feature: Release Notes
TQID: 'https://experienceleague.adobe.com/38I3U5y9rmurP5gVhalfUq7DlcUb-JpF5eUam1nwEyk'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 6b3a77ca95f7de23f044e531f1639c1aee1bbcef
workflow-type: tm+mt
source-wordcount: 236
ht-degree: 1%

---

# [!DNL Commerce Version Tool]发行说明

这些发行说明描述了[!DNL Commerce Version Tool] ([!DNL CVT])的更新。

为最新发布提供支持。 提供了旧版本的发行说明以供参考。
更新包括：

![新](../../assets/new.svg)新功能
![修复](../../assets/fix.svg)修复和改进
![错误](../../assets/bug.svg)已知问题

## 版本1.0.2 — 2026年8月 {#version-1-0-2}

### 新增功能

![新](../../assets/new.svg) **编辑器`replace`支持** — 添加了对通过编辑器`replace`删除核心模块的安装的支持，提高了这些模块的修补程序检测准确性。<!-- ACSEC-527 -->

## 版本1.0.0 — 2026年6月 {#version-1-0-0}

![新](../../assets/new.svg)更新包括：
- **修补程序状态报告** — 报告Adobe Commerce安装应用了、缺少或无法分类的每月Adobe Commerce安全修补程序。
- **CVE保护状态** — 将修补程序结果映射到每个CVE保护状态值： `PROTECTED`、`VULNERABLE`、`UNKNOWN`和`NOT_APPLICABLE`。
- **多组件支持** — 从`composer.lock`中检测已安装的Adobe Commerce组件，包括Adobe Commerce企业对企业(B2B)、Adobe Commerce Page Builder、Adobe Commerce Inventory以及修补程序注册表文件中表示的其他组件。
- **JSON和CSV输出** — 默认情况下为程序化使用提供JSON输出，为电子表格、扫描仪、仪表板和合规性工具提供CSV输出。
- **脱机友好缓存行为** — 每次成功获取后，在本地缓存修补程序注册表文件。 如果远程注册表不可用，[!DNL CVT]工具可以使用缓存的注册表并发出警告。
- **捆绑投放** — 每月在Adobe Commerce安全修补程序文件中提供。 应用修补程序会在`vendor/bin/patch-status`处安装[!DNL CVT]，而不执行单独的安装步骤。

## 相关主题

- [简介](intro.md)
- [生成修补程序状态报告](generate-report.md)
- [故障排除](troubleshooting.md)
