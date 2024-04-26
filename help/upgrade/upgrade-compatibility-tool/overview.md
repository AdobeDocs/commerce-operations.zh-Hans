---
title: 概述 [!DNL Upgrade Compatibility Tool]
description: 了解 [!DNL Upgrade Compatibility Tool] 以及它如何帮助您实施Adobe Commerce项目。
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: fc1be3362863d3b0fa3468380fe62ca698abac43
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 指南概述

{{commerce-only}}

本指南适用于Adobe Commerce的管理员和软件工程师。 它包含有关安装的 [!DNL Upgrade Compatibility Tool]，以及其配置和管理。 它假定您对核心Commerce配置和功能有基本的了解。

## 概述 [!DNL Upgrade Compatibility Tool]

此 [!DNL Upgrade Compatibility Tool] 是一种工具，用于通过分析其中安装的所有模块和核心代码，根据特定版本检查Adobe Commerce自定义实例。 它会返回在升级到新版Adobe Commerce之前必须解决的严重问题、错误和警告列表。

## 使用 [!DNL Upgrade Compatibility Tool]

您可以使用 [!DNL Upgrade Compatibility Tool] 通过：

- 作为独立 [命令行界面](../upgrade-compatibility-tool/run.md) 工具。 有关可用命令的完整列表，请参见 [`bin/uct` 引用](../../tools/reference/uct.md).
- 集成 [!DNL Upgrade Compatibility Tool] 使用 [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- 内的运行配置 [MagentoPHPStorm插件](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## 工作流

下图显示了运行工作流时可能的工作流 [!DNL Upgrade Compatibility Tool]：

![[!DNL Upgrade Compatibility Tool] 图表](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] 演示

观看本视频以了解 [!DNL Upgrade Compatibility Tool]：

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## 帮助改进 [!DNL Upgrade Compatibility Tool]

如果您需要本指南中未涉及的信息或问题，请使用以下资源：

要与 [!DNL Upgrade Compatibility Tool] 团队，通过工程Slack渠道联系我们 [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). 我们希望听到您的反馈、问题和建议，以帮助我们改进该工具。

此 [!DNL Upgrade Compatibility Tool] 使用的规则定义于 [编码标准](https://developer.adobe.com/commerce/php/coding-standards/) 确保您的项目遵循Adobe Commerce最佳实践，并帮助您改进和扩展 [!DNL Upgrade Compatibility Tool].

请参阅 [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) 主题，以了解有关对编码标准做出贡献的更多信息。

## 资源

请参阅以下资源以帮助您了解Adobe Commerce升级：

- 此 [升级指南](../overview.md) 概述了典型的Adobe Commerce升级历程以及在该历程中遵循的最佳实践。
- 此 [即将发布的版本](https://devdocs.magento.com/release/) 页面提供计划版本和即将发布的版本的日期。
- 此 [社区资源](https://developer.adobe.com/commerce/contributor/community/) 页面用于开始讨论，或查找更多信息。
- 查看 [相关工具](../upgrade-compatibility-tool/related-tools.md) 页面，了解典型升级历程中的有用工具。
