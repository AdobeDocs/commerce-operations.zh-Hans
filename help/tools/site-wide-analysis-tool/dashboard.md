---
title: '[!DNL Dashboard]'
description: 了解 [!DNL Dashboard] 选项卡 [!DNL Site-Wide Analysis Tool]、元素、使用时间、好处和最佳实践。
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

此 [!UICONTROL Dashboard] 页面显示概览 [!DNL widgets] 那个提供Adobe Commerce网站运行状况和当前状态的“单一窗口视图”。 每个 [!DNL widget] 包含指向每个功能页面、每个工具本身或报表(取决于 [!DNL widget])。
此外，还有一个列表 [!UICONTROL External Resources] Adobe Commerce的链接，包括 [Adobe Commerce帮助中心支持知识库（帮助中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)， [Adobe Commerce开发人员文档(DevDocs)](https://developer.adobe.com/commerce/docs/)， [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}， [安全中心](https://helpx.adobe.com/security.html)、和 [Adobe Commerce观察(OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## 元素

* **[!UICONTROL Recommendations]**：显示网站的最佳实践推荐。 Recommendations（发现的问题和要修复的建议）按优先级排序 — P0（严重）到P4（通知）。
Recommendations包括描述、推荐、网站影响、根本原因、方案/先决条件和使用的工具。

* **[!UICONTROL Upgrade Compatibility Tool]**：通过分析其中安装的所有模块和核心代码，针对特定版本检查Adobe Commerce自定义实例。 它会返回在升级到最新版本的Adobe Commerce之前必须解决的严重问题、错误和警告列表。 它还标识了在尝试升级到新版Adobe Commerce之前必须在代码中修复的潜在问题。
此 [!UICONTROL Upgrade Compatibility Tool] 允许您标识何时对自定义功能进行了核心代码更改。

* **[!UICONTROL Security Center Widget]**：显示网站的安全分析。
显示的安全信息包括 [技术 [!DNL Stack] 版本符合性 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] 安全最佳实践Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
此 [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) 监控Adobe Commerce站点的安全风险。 它可以主动高效地检测商家商店中的恶意软件，并在存在任何安全风险、恶意软件或威胁时通知商家，还可以识别丢失的Adobe Commerce补丁和更新。

* **[!UICONTROL Extensions]**：显示当前在Adobe Commerce实例上安装的扩展。 [Adobe Commerce市场](https://marketplace.magento.com/extensions.html) 如果可用，将为该处列出的扩展提供相关信息。

* **[!UICONTROL Alerts]**：显示最新版本 [!DNL New Relic Managed Alerts] 对于Adobe Commerce实例。 了解有关 [Adobe Commerce的受管警报](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) 以及操作方法 [访问New Relic服务](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) 在Adobe Commerce支持知识库中。

* **[!UICONTROL Non-recommended software in use]**：根据您的Adobe Commerce版本，显示您的Adobe Commerce实例当前使用的非推荐软件。 非推荐软件列在 [!UICONTROL Name]， [!UICONTROL Installed Version]、和 [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**：根据您可能已安装的修补程序和Adobe Commerce版本，显示任何建议的修补程序的简短列表。 推荐修补程序的完整列表可在 **[!UICONTROL Patches]** 功能选项卡，此选项卡也位于 [!DNL Site-Wide Analysis Tool]. 修补程序由 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. 列出的所有修补程序都与您当前的Adobe Commerce实例兼容。
如果没有为Adobe Commerce实例显示的建议修补程序，则 [!DNL widget] 将显示为， **[!UICONTROL No Recommended Patches]**.

## 使用时间

此 **[!UICONTROL Dashboard]** 页面是您在 [!DNL Site-Wide Analysis Tool] 不仅能够轻松查看网站整体健康的“概览”，而且您还可以通过每个页面查看和访问Adobe Commerce网站的特定工具、建议和报告 [!DNL widget].

## 优点

* 此 [!DNL widgets] 对象 [!UICONTROL Security Center]， [!UICONTROL Recommendations]， [!UICONTROL Extensions]、和 [!UICONTROL Security Scan] 所有方法都使用易于阅读的颜色编码的交互式圆形图，图表一侧有图例，中间有计数总计，表示有多少个 [!UICONTROL Recommendations]， [!UICONTROL Extensions]、和 [!UICONTROL Security Scan Tool] 每个功能具有的项目。 [!UICONTROL Recommendations] 和 [!UICONTROL Security Scan Tool] 图表按严重性分隔。 [!UICONTROL Extensions] 分为四个分类：当前版本、旧版本、已禁用和未知。

* [!DNL New Relic Alerts] 顶部列出了最新警报，其中包括简短描述以及警报发生的时间。

* 此 [!UICONTROL Recommendations] 和 [!UICONTROL Extensions] [!DNL widgets] 通过单击，可以访问每个功能的完整数据页面 **[!UICONTROL View All]**.

* 此 [!UICONTROL Security Scan Tool] 具有 **[!UICONTROL View Report]** 中的链接 [!DNL widget] 将您转到 [!UICONTROL Recommendations] 页面。

* 此 [!DNL Upgrade Compatibility Tool] 具有 **[!UICONTROL Run Upgrade Scan]** 中的按钮 [!DNL widget] 窗口。

## 使用的最佳实践 [!UICONTROL Dashboard]

* 单击每个 [!DNL widget] 访问它提供的详细数据，从而获取对网站安全性、运行状况、建议和改进网站的最佳实践的洞察和了解。

* 转到 [!UICONTROL Security Scan Tool] [!DNL widget] 并单击 [!UICONTROL View Report] 查看 [!UICONTROL Recommendations] 您的网站的报告。

* 使用 [!DNL External Resources] 这些链接可用于了解更多信息、及时了解安全修补程序、更新和最佳实践，或利用 [Adobe Commerce帮助中心支持知识库（帮助中心）](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html)， [Adobe Commerce开发人员文档(DevDocs)](https://developer.adobe.com/commerce/docs/)， [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}， [安全中心](https://helpx.adobe.com/security.html)、和 [Adobe Commerce观察(OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
