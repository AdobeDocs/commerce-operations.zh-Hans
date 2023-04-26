---
title: '[!DNL Dashboard]'
description: 了解 [!DNL Dashboard] 选项卡 [!DNL Site-Wide Analysis Tool]、元素、使用时间、优势和最佳实践。
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

的 [!UICONTROL Dashboard] 页面显示概览 [!DNL widgets] “单一的玻璃窗视图”，可显示Adobe Commerce网站的运行状况和当前状态。 每个 [!DNL widget] 包含指向每个功能页面、每个工具本身或报表(具体取决于 [!DNL widget])。
还有一个列表 [!UICONTROL External Resources] Adobe Commerce的链接，包括 [Adobe Commerce帮助中心支持知识库（帮助中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce开发人员文档(DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]:搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [安全中心](https://helpx.adobe.com/security.html)和 [Adobe Commerce观察](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## 元素

* **[!UICONTROL Recommendations]**:显示网站的最佳实践推荐。 Recommendations（发现的问题和要修复的建议）按优先级(P0（关键）到P4（通知）)进行排序。
Recommendations包括描述、推荐、站点影响、根本原因、方案/先决条件以及使用的工具。

* **[!UICONTROL Upgrade Compatibility Tool]**:通过分析特定版本中安装的所有模块和核心代码，检查Adobe Commerce自定义实例。 它会返回一个关键问题、错误和警告的列表，在升级到最新版本的Adobe Commerce之前，必须解决这些问题。 它还会识别在尝试升级到较新版本的Adobe Commerce之前，必须在代码中修复的潜在问题。
的 [!UICONTROL Upgrade Compatibility Tool] 允许您识别何时对自定义功能进行了核心代码更改。

* **[!UICONTROL Security Center Widget]**:显示网站的安全分析。
显示的安全信息包括 [技术 [!DNL Stack] 版本合规性 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] 最佳实践安全性Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
的 [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) 监控Adobe Commerce站点的安全风险。 它能够主动、高效地检测商家商店上的恶意软件，并在存在任何安全风险、恶意软件或威胁时通知商家，并能够识别缺失的Adobe Commerce补丁和更新。

* **[!UICONTROL Extensions]**:显示当前在您的Adobe Commerce实例上安装的扩展。 [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) 如果可用，将为此处列出的扩展提供信息。

* **[!UICONTROL Alerts]**:显示最新 [!DNL New Relic Managed Alerts] 例如Adobe Commerce实例。 详细了解 [适用于Adobe Commerce的托管警报](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) 和如何 [访问New Relic服务](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) 在Adobe Commerce支持知识库中。

* **[!UICONTROL Non-recommended software in use]**:根据您的Adobe Commerce版本，显示您的Adobe Commerce实例当前正在使用的非推荐软件。 不推荐的软件由 [!UICONTROL Name], [!UICONTROL Installed Version]和 [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**:根据您可能已安装的修补程序和Adobe Commerce版本，显示所有推荐修补程序的简短列表。 在 **[!UICONTROL Patches]** 功能选项卡，该选项卡也位于 [!DNL Site-Wide Analysis Tool]. 修补程序由 [[!DNL Quality Patches Tool]:搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. 列出的所有修补程序都与您当前的Adobe Commerce实例兼容。
如果没有可为Adobe Commerce实例显示的推荐修补程序，则 [!DNL widget] 将显示， **[!UICONTROL No Recommended Patches]**.

## 何时使用

的 **[!UICONTROL Dashboard]** page是您在 [!DNL Site-Wide Analysis Tool] 您不仅可以轻松查看网站整体运行状况的“大图”，还可以通过每个网站查看和访问Adobe Commerce网站的特定工具、建议和报表 [!DNL widget].

## 优点

* 的 [!DNL widgets] 表示 [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions]和 [!UICONTROL Security Scan] 所有图形都使用易于阅读的彩色编码交互式圆形图，侧边有图例，中心有总计，用于表示有多少个图例 [!UICONTROL Recommendations], [!UICONTROL Extensions]和 [!UICONTROL Security Scan Tool] 每个功能都包含的项目。 [!UICONTROL Recommendations] 和 [!UICONTROL Security Scan Tool] 图表按严重性分隔。 [!UICONTROL Extensions] 分为四类：当前版本、旧版本、已禁用和未知。

* [!DNL New Relic Alerts] 将列出最近的警报，其中包括简短的描述以及警报发生的时间。

* 的 [!UICONTROL Recommendations] 和 [!UICONTROL Extensions] [!DNL widgets] 可通过单击 **[!UICONTROL View All]**.

* 的 [!UICONTROL Security Scan Tool] 具有 **[!UICONTROL View Report]** 链接 [!DNL widget] 窗口 [!UICONTROL Recommendations] 页面。

* 的 [!DNL Upgrade Compatibility Tool] 具有 **[!UICONTROL Run Upgrade Scan]** 按钮 [!DNL widget] 窗口。

## 使用的最佳实践 [!UICONTROL Dashboard]

* 单击 [!DNL widget] 要访问它提供的详细数据，可深入了解和了解您网站的安全性、运行状况、建议以及改进网站的最佳实践。

* 转到 [!UICONTROL Security Scan Tool] [!DNL widget] 单击 [!UICONTROL View Report] 查看 [!UICONTROL Recommendations] 报表。

* 使用 [!DNL External Resources] 链接可以了解更多信息、了解最新的安全修补程序、更新和最佳实践，或利用 [Adobe Commerce帮助中心支持知识库（帮助中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce开发人员文档(DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]:搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [安全中心](https://helpx.adobe.com/security.html)和 [Adobe Commerce观察](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
