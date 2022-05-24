---
title: “集成 [!DNL Site-Wide Analysis Tool]"
description: 按照以下步骤检索 [!DNL Upgrade Compatibility Tool] 报表 [!DNL Site-Wide Analysis Tool] 功能板。Adobe Commerce项目
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# 集成 [!DNL Site-Wide Analysis Tool]

的 [!DNL Site-Wide Analysis Tool] 提供24/7实时性能监控、报告和建议，以确保Adobe Commerce安装的安全性和可操作性。

的 [!DNL Upgrade Compatibility Tool] 现已与集成 [!DNL Site-Wide Analysis Tool] 以便让非技术人员能够 [!DNL Upgrade Compatibility Tool] 然后 [HTML报表](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en#output) 包含每个文件的问题列表，以指定其严重性、错误代码和错误描述。

请参阅 [[!DNL Site-Wide Analysis Tool] 用户指南](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) 以了解更多信息。

## 运行 [!DNL Upgrade Compatibility Tool] 从特警队

导航到 [!DNL Site-Wide Analysis Tool] 功能板，然后找到 [!DNL Upgrade Compatibility Tool] 小组件。

![UCT SWAT小组件 — 初始](../../assets/upgrade-guide/uct-swat-initial.png)

单击 **[!UICONTROL Run Upgrade Scan]**. 扫描可能需要一些时间，具体取决于项目大小。 旋转器指示扫描正在进行。

![UCT SWAT小组件 — 正在进行](../../assets/upgrade-guide/uct-swat-progress.png)

扫描完成后，小组件中会显示高级结果。

![UCT SWAT小组件 — 结果](../../assets/upgrade-guide/uct-swat-results.png)

单击 **[!UICONTROL Download Report]** 检索 [!DNL Upgrade Compatibility Tool] HTML报告并查看详细信息。
