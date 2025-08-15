---
title: '[!DNL Site-Wide Analysis Tool]'
description: 了解 [!DNL Site-Wide Analysis] 工具、其用途、安装过程以及如何获取访问权限
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 5f39a2d8440225b3a2e463894e2bd866196fbac2
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>自2024年4月23日起，所有Adobe Commerce本地客户都将停用[!DNL Site-Wide Analysis Tool]。

本指南提供了[!DNL Site-Wide Analysis Tool]的整体概述。 它介绍了安装的使用和分步说明，以及如何访问该工具。

## 什么是[!DNL Site-Wide Analysis Tool]？

[!DNL Site-Wide Analysis Tool]是一个主动式自助服务工具和中央存储库，其中包含详细的系统分析和建议，以确保Adobe Commerce安装的安全性和可操作性。 它提供全天候的实时性能监控、报告和建议，以发现潜在问题并更好地了解站点运行状况、安全性和应用程序配置。 它有助于缩短解决时间并提高站点稳定性和性能。

![站点范围分析工具仪表板](../../assets/tools/swat-dashboard.png){zoomable="yes"}

观看此[简介视频](https://www.youtube.com/watch?v=KW2R8ki_RG4)以了解更多信息。

## 工具概述

- **仪表板**
   - 显示系统的整体运行状况，包括检测到的问题的通知以及按优先级列出的特定建议。<br>
它还包含一个历史图表，用于跟踪网站运行状况随时间的变化。
   - 显示允许您访问的&#x200B;**[!UICONTROL Security Center Widget]**：
      - [技术 [!DNL Stack] 版本合规性符合 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)
      - [Adobe安全公告](https://helpx.adobe.com/security/security-bulletin.html)
      - 来自[的 [!DNL Security Scan Tool]推荐](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html)
      - [[!DNL Site-Wide Analysis Tool] 最佳实践安全建议](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html)

- **信息** — 提供客户联系信息和当前票证的摘要，以及有关每个已安装的Adobe Commerce产品的详细信息。

- **建议** — 列出基于最佳实践的建议，以解决在您的网站上检测到的问题：
   - 对于需要更新基础结构的更改，请提交支持请求。
   - 对于需要更新应用程序的更改，请自行进行更改。
   - 对于需要手动干预的更改（如[代码部署](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow)），请向系统管理员或开发人员寻求帮助。

- **异常** — 列出由异常条件引起的应用程序引发的错误，并且没有错误处理程序。

- **扩展** — 列出所有第三方扩展和第三方库。

- **修补程序** — 与[!DNL Quality Patches Tool]集成，它提供特定于您的Adobe Commerce实例的所有可用修补程序的列表。

## 与其他Adobe Commerce支持工具的集成

在一个位置查看有关您网站的所有重要见解。 [!DNL Site-Wide Analysis Tool]允许您从[!UICONTROL Security Center Widget]、[!DNL Upgrade Compatability Tool]和[!DNL Managed Alerts]直接访问和获取信息。

- [**[!UICONTROL Security Center Widget]**] — 显示网站的安全分析。<br>
显示的安全信息包括[技术 [!DNL Stack] 版本合规性，符合 [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] 最佳实践安全建议](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html)。<br>
[[!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html)通过主动检测恶意软件并在其存储遭到破坏时通知他们，为Adobe Commerce和Magento Open-Source客户提供了对其存储的安全状态的实时洞察。

- [**[!DNL Upgrade Compatability Tool]**](../../upgrade/upgrade-compatibility-tool/overview.md) — 针对目标升级版本运行Adobe Commerce的自定义实例，并返回必须解决的严重问题、错误和警告的摘要，从而使升级分析过程更简单、更快、更便宜。

- [**[!DNL Managed Alerts]**](https://support.magento.com/hc/en-us/sections/360010758472-Managed-alerts-for-Adobe-Commerce) — 监控多个量度以主动跟踪平台的性能，并提供有关如何排查问题的具体说明，以便商家能够避免严重停机并及时了解其CPU、应用程序性能、磁盘、内存和数据库。

## 本指南面向谁？

希望提高其Adobe Commerce网站可见度的商家和合作伙伴。 它使商家能够改善其客户体验，并在最佳实践建议和基本问题上更紧密地保持一致。

## [!DNL Site-Wide Analysis Tool]演示

观看此视频以了解[!DNL Site-Wide Analysis Tool]：

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
