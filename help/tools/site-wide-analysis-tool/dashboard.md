---
title: '[!DNL Dashboard]'
description: 了解 [!DNL Site-Wide Analysis Tool]元素中的 [!DNL Dashboard] 选项卡、使用时间、优势和最佳实践。
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

[!UICONTROL Dashboard]页面显示概览[!DNL widgets]，它提供了Adobe Commerce网站的运行状况和当前状态的“单一窗格”。 每个[!DNL widget]都包含一个访问链接，指向每个功能的页面、每个工具本身或报告（具体取决于[!DNL widget]）。
还有[!UICONTROL External Resources]个Adobe Commerce链接列表，包括[Adobe Commerce帮助中心支持知识库（帮助中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=zh-Hans)、[Adobe Commerce开发人员文档(DevDocs)](https://developer.adobe.com/commerce/docs/)、[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans){target="_blank"}、[安全中心](https://helpx.adobe.com/cn/security.html)和[Adobe Commerce (OAC)观察](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=zh-Hans)。

## 元素

* **[!UICONTROL Recommendations]**：显示网站的最佳实践推荐。 Recommendations（发现的问题和要修复的建议）按优先级排序 — P0（严重）到P4（通知）。
Recommendations包括描述、推荐、网站影响、根本原因、方案/先决条件和使用的工具。

* **[!UICONTROL Upgrade Compatibility Tool]**：通过分析其中安装的所有模块和核心代码，针对特定版本检查Adobe Commerce自定义实例。 它会返回在升级到最新版本的Adobe Commerce之前必须解决的严重问题、错误和警告列表。 它还标识了在尝试升级到新版Adobe Commerce之前必须在代码中修复的潜在问题。
[!UICONTROL Upgrade Compatibility Tool]允许您识别何时对自定义功能进行了核心代码更改。

* **[!UICONTROL Security Center Widget]**：显示网站的安全分析。
显示的安全信息包括[Tech [!DNL Stack] 版本合规性与 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=zh-Hans), [Adobe Security Bulletin](https://helpx.adobe.com/cn/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=zh-Hans), and [[!DNL Site-Wide Analysis Tool] Best Practice Security Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=zh-Hans)。<br>
[[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=zh-Hans)监控Adobe Commerce站点的安全风险。 它可以主动高效地检测商家商店中的恶意软件，并在存在任何安全风险、恶意软件或威胁时通知商家，还可以识别丢失的Adobe Commerce补丁和更新。

* **[!UICONTROL Extensions]**：显示当前安装在Adobe Commerce实例上的扩展。 为此处列出的扩展提供了[Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html)信息（如果可用）。

* **[!UICONTROL Alerts]**：显示Adobe Commerce实例的最新[!DNL New Relic Managed Alerts]。 在Adobe Commerce支持知识库中了解有关[Adobe Commerce托管警报](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html?lang=zh-Hans)以及如何[访问New Relic服务](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html?lang=zh-Hans)的更多信息。

* **[!UICONTROL Non-recommended software in use]**：根据您的Adobe Commerce版本，显示您的Adobe Commerce实例当前使用的非推荐软件。 非推荐软件由[!UICONTROL Name]、[!UICONTROL Installed Version]和[!UICONTROL Recommended Version]列出。

* **[!UICONTROL Recommended Patches]**：根据您可能已安装的修补程序和Adobe Commerce版本，显示任何建议的修补程序的简短列表。 建议修补程序的完整列表可在&#x200B;**[!UICONTROL Patches]**&#x200B;功能选项卡上找到，该选项卡也位于[!DNL Site-Wide Analysis Tool]中。 修补程序由[[!DNL Quality Patches Tool]提供：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans){target="_blank"}。 列出的所有修补程序都与您当前的Adobe Commerce实例兼容。
如果没有为Adobe Commerce实例显示的建议修补程序，则将显示此[!DNL widget] **[!UICONTROL No Recommended Patches]**。

## 使用时间

**[!UICONTROL Dashboard]**&#x200B;页面是您在[!DNL Site-Wide Analysis Tool]中的概览命令中心，不仅能够轻松查看网站整体运行状况的“概览”，而且您还可以通过每个[!DNL widget]查看和访问Adobe Commerce网站的特定工具、建议和报告。

## 优点

* [!UICONTROL Security Center]、[!UICONTROL Recommendations]、[!UICONTROL Extensions]和[!UICONTROL Security Scan]的[!DNL widgets]都使用易于阅读的带有图形图例的颜色编码交互式循环图，其中心包含总计，以表示每个功能有多少个[!UICONTROL Recommendations]、[!UICONTROL Extensions]和[!UICONTROL Security Scan Tool]项。 [!UICONTROL Recommendations]和[!UICONTROL Security Scan Tool]图形按严重性分隔。 [!UICONTROL Extensions]分为四个分类：当前版本、旧版本、已禁用和未知。

* [!DNL New Relic Alerts]列表顶部列出了最新警报，包括简短描述以及警报发生的时间。

* [!UICONTROL Recommendations]和[!UICONTROL Extensions] [!DNL widgets]通过单击&#x200B;**[!UICONTROL View All]**&#x200B;可访问每个功能的完整数据页。

* [!UICONTROL Security Scan Tool]在[!DNL widget]窗口中有一个&#x200B;**[!UICONTROL View Report]**&#x200B;链接，可将您转到[!UICONTROL Recommendations]页面。

* [!DNL Upgrade Compatibility Tool]的[!DNL widget]窗口中有一个&#x200B;**[!UICONTROL Run Upgrade Scan]**&#x200B;按钮。

## 使用[!UICONTROL Dashboard]的最佳实践

* 单击每个[!DNL widget]可访问其提供的详细数据，从而深入了解和了解网站的安全性、运行状况、推荐以及改进网站的最佳实践。

* 转到[!UICONTROL Security Scan Tool] [!DNL widget]并单击[!UICONTROL View Report]以查看网站的[!UICONTROL Recommendations]报告。

* 使用[!DNL External Resources]链接可了解更多信息、保持最新的安全修补程序、更新和最佳实践，或利用[Adobe Commerce帮助中心支持知识库（帮助中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=zh-Hans)、[Adobe Commerce开发人员文档(DevDocs)](https://developer.adobe.com/commerce/docs/)、[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans){target="_blank"}、[安全中心](https://helpx.adobe.com/cn/security.html)以及[Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=zh-Hans)的观察。
