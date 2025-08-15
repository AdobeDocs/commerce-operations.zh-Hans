---
title: ' [!DNL Upgrade Compatibility Tool]概述'
description: 了解 [!DNL Upgrade Compatibility Tool] 以及它如何帮助您完成您的Adobe Commerce项目。
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 指南概述

{{commerce-only}}

本指南适用于Adobe Commerce的管理员和软件工程师。 它包含有关[!DNL Upgrade Compatibility Tool]的安装及其配置和管理的详细信息。 它假定您对核心Commerce配置和功能有基本的了解。

## [!DNL Upgrade Compatibility Tool]概述

[!DNL Upgrade Compatibility Tool]是一种通过分析其中安装的所有模块和核心代码来针对特定版本检查Adobe Commerce自定义实例的工具。 它会返回在升级到新版Adobe Commerce之前必须解决的严重问题、错误和警告列表。

## 使用[!DNL Upgrade Compatibility Tool]

您可以通过以下方式使用[!DNL Upgrade Compatibility Tool]：

- 作为独立[命令行界面](../upgrade-compatibility-tool/run.md)工具。 有关可用命令的完整列表，请参阅[`bin/uct`引用](../../tools/reference/uct.md)。
- 将[!DNL Upgrade Compatibility Tool]与[[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md)集成。
- [Magento PHPStorm插件](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md)中的运行配置。

## 工作流

下图显示了运行[!DNL Upgrade Compatibility Tool]时可能的工作流：

![[!DNL Upgrade Compatibility Tool]图表](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool]演示

观看此视频以了解[!DNL Upgrade Compatibility Tool]：

>[!VIDEO](https://video.tv.adobe.com/v/344381?quality=12&captions=chi_hans)

## 帮助改进[!DNL Upgrade Compatibility Tool]

如果您需要本指南中未涉及的信息或问题，请使用以下资源：

要与[!DNL Upgrade Compatibility Tool]团队建立联系，请通过工程Slack渠道[#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F)联系我们。 我们希望听到您的反馈、问题和建议，以帮助我们改进该工具。

[!DNL Upgrade Compatibility Tool]使用我们[编码标准](https://developer.adobe.com/commerce/php/coding-standards/)中定义的规则来确保您的项目遵循Adobe Commerce最佳实践，并帮助您改进和扩展[!DNL Upgrade Compatibility Tool]。

有关参与编码标准的详细信息，请参阅[Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/)主题。

## 资源

请参阅以下资源以帮助您了解Adobe Commerce升级：

- [升级指南](../overview.md)概述了典型的Adobe Commerce升级历程以及在该历程中遵循的最佳实践。
- [即将发布的版本](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/planning/schedule)页面提供了计划版本和即将发布的版本的日期。
- [社区资源](https://developer.adobe.com/commerce/contributor/community/)页面将放置以开始讨论，或查找更多信息。
- 查看[相关工具](../upgrade-compatibility-tool/related-tools.md)页面，了解典型升级历程中的有用工具。
