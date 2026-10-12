---
title: 集成[!DNL Site-Wide Analysis Tool]
description: 按照以下步骤在您的Adobe Commerce项目中从[!DNL Site-Wide Analysis Tool]仪表板检索[!DNL Upgrade Compatibility Tool]报告。
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%
---
# 集成[!DNL Site-Wide Analysis Tool]

[!DNL Site-Wide Analysis Tool]提供全天候的实时性能监控、报告和建议，以确保Adobe Commerce实例的安全性和可操作性。

[!DNL Upgrade Compatibility Tool]现在与[!DNL Site-Wide Analysis Tool]集成，以便非技术人员能够运行[!DNL Upgrade Compatibility Tool]并获得包含每个文件问题列表的[报告](../upgrade-compatibility-tool/reports.md)。

有关详细信息，请参阅[[!DNL Site-Wide Analysis Tool] 用户指南](/help/tools/site-wide-analysis-tool/access.md)。

## 从[!DNL Site-Wide Analysis Tool]运行[!DNL Upgrade Compatibility Tool]

导航到项目的[!DNL Site-Wide Analysis Tool]仪表板并找到[!DNL Upgrade Compatibility Tool]小组件。

![UCT SWAT小组件 — 初始](../../assets/upgrade-guide/uct-swat-initial.png)

单击&#x200B;**[!UICONTROL Run Upgrade Scan]**。 扫描可能需要一些时间，具体取决于项目大小。 旋转图标表示扫描正在进行中。

![UCT SWAT小组件 — 进行中](../../assets/upgrade-guide/uct-swat-progress.png)

扫描完成后，将在构件中显示高级别结果。

![UCT SWAT小组件 — 结果](../../assets/upgrade-guide/uct-swat-results.png)

单击&#x200B;**[!UICONTROL Download Report]**&#x200B;以检索[!DNL Upgrade Compatibility Tool] [HTML报告](../upgrade-compatibility-tool/reports.md#html-report)并查看详细信息。


>[!NOTE]
>
> 通过[!DNL Site-Wide Analysis Tool]运行[!DNL Upgrade Compatibility Tool]可优化您的结果，并帮助您关注目标升级中新的和关键的问题。 它使用[`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results)选项，并始终显示将您的项目版本与最新发布版本进行比较的结果。
