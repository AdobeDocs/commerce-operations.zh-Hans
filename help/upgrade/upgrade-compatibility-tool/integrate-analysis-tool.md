---
title: 集成 [!DNL Site-Wide Analysis Tool]
description: 按照以下步骤检索 [!DNL Upgrade Compatibility Tool] 报告来源 [!DNL Site-Wide Analysis Tool] 您的Adobe Commerce项目上的仪表板。
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# 集成 [!DNL Site-Wide Analysis Tool]

此 [!DNL Site-Wide Analysis Tool] 提供7天24小时的实时性能监控、报告和建议，以确保Adobe Commerce实例的安全性和可操作性。

此 [!DNL Upgrade Compatibility Tool] 现已与 [!DNL Site-Wide Analysis Tool] 以便让非技术人员能够运行 [!DNL Upgrade Compatibility Tool] 并获取 [报告](../upgrade-compatibility-tool/reports.md) 包含每个文件的问题列表。

请参阅 [[!DNL Site-Wide Analysis Tool] 用户指南](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) 了解更多信息。

## 运行 [!DNL Upgrade Compatibility Tool] 从 [!DNL Site-Wide Analysis Tool]

导航到 [!DNL Site-Wide Analysis Tool] 您的项目的仪表板，并找到 [!DNL Upgrade Compatibility Tool] 构件。

![UCT SWAT小组件 — 初始](../../assets/upgrade-guide/uct-swat-initial.png)

单击 **[!UICONTROL Run Upgrade Scan]**. 扫描可能需要一些时间，具体取决于项目大小。 旋转图标表示扫描正在进行中。

![UCT SWAT小组件 — 进行中](../../assets/upgrade-guide/uct-swat-progress.png)

扫描完成后，将在Widget中显示高级结果。

![UCT SWAT小组件 — 结果](../../assets/upgrade-guide/uct-swat-results.png)

单击 **[!UICONTROL Download Report]** 以检索 [!DNL Upgrade Compatibility Tool] [HTML报告](../upgrade-compatibility-tool/reports.md#html-report) 并查看详细信息。


>[!NOTE]
>
> 运行 [!DNL Upgrade Compatibility Tool] 通过 [!DNL Site-Wide Analysis Tool] 优化结果，并帮助您重点解决对Target升级来说是新的和关键的问题。 它使用 [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) 选项并始终显示将项目版本与最新发布版本进行比较的结果。
