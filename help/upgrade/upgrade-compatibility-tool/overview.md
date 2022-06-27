---
title: “概述 [!DNL Upgrade Compatibility Tool]"
description: 了解 [!DNL Upgrade Compatibility Tool] 以及它如何帮助您完成Adobe Commerce项目。
source-git-commit: 9b0f97d36092d2a1057cdc905671cda8540881c9
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# 指南概述

{{commerce-only}}

本指南面向Adobe Commerce的管理员和软件工程师。 其中包含有关安装 [!DNL Upgrade Compatibility Tool]，以及其配置和管理。 该指南假定您基本了解核心商务配置和功能。

## 概述 [!DNL Upgrade Compatibility Tool]

的 [!DNL Upgrade Compatibility Tool] 是一个工具，可通过分析Adobe Commerce中安装的所有模块和核心代码，根据特定版本检查该自定义实例。 它会返回一个关键问题、错误和警告的列表，在升级到较新版本的Adobe Commerce之前，必须解决这些问题。

## 使用 [!DNL Upgrade Compatibility Tool]

您可以使用 [!DNL Upgrade Compatibility Tool] 通过：

- 作为独立 [命令行界面](../upgrade-compatibility-tool/run.md) 工具。
- 集成 [!DNL Upgrade Compatibility Tool] 和 [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- 中的运行配置 [MagentoPHPStorm插件](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## 工作流

下图显示了运行 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 图表](../../assets/upgrade-guide/uct-diagram-v5.png)

## 帮助改进 [!DNL Upgrade Compatibility Tool]

如果您需要信息或遇到本指南未涵盖的问题，请使用以下资源：

与 [!DNL Upgrade Compatibility Tool] 团队，通过工程Slack渠道与我们联系 [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). 我们希望听取您的反馈、问题和建议，以帮助我们改进该工具。

的 [!DNL Upgrade Compatibility Tool] 使用 [编码标准](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) 以确保您的项目遵循Adobe Commerce最佳实践，并帮助您改进和扩展 [!DNL Upgrade Compatibility Tool].

请参阅 [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html) 主题以了解有关贡献编码标准的更多信息。

## 资源

请参阅以下资源以帮助您了解Adobe Commerce升级：

- 的 [升级指南](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) 概述典型的Adobe Commerce或Magento Open Source升级历程以及跟踪该历程的最佳实践。
- 的 [即将发行的版本](https://devdocs.magento.com/release/) 页面提供了计划版本和即将发行版本的日期。
- 的 [社区资源](https://developer.adobe.com/commerce/contributor/community/) 页面用于开始讨论或查找更多信息。
- 检查 [相关工具](../upgrade-compatibility-tool/related-tools.md) 页面，了解典型升级历程中的有用工具。
