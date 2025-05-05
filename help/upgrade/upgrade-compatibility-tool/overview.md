---
title: ' [!DNL Upgrade Compatibility Tool]概述'
description: 了解 [!DNL Upgrade Compatibility Tool] 及其如何帮助您处理Adobe Commerce项目。
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 指南概述

{{commerce-only}}

本指南面向Adobe Commerce管理员和软件工程师。 它包含有关[!DNL Upgrade Compatibility Tool]安装及其配置和管理的详细信息。 本课程假定您对Commerce核心配置和功能有基本了解。

## [!DNL Upgrade Compatibility Tool]概述

[!DNL Upgrade Compatibility Tool]是一种工具，它通过分析安装在Adobe Commerce自定义实例中的所有模块和核心代码来根据特定版本检查该实例。 它返回在升级到较新版本的Adobe Commerce之前必须解决的关键问题、错误和警告的列表。

## 使用[!DNL Upgrade Compatibility Tool]

您可以通过以下方式使用[!DNL Upgrade Compatibility Tool]：

- 作为独立的[命令行界面](../upgrade-compatibility-tool/run.md)工具。 有关可用命令的完整列表，请参阅[`bin/uct`引用](../../tools/reference/uct.md)。
- 正在将[!DNL Upgrade Compatibility Tool]与[[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md)集成。
- [MagentoPHPStorm插件](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md)内的运行配置。

## 工作流

下图显示了运行[!DNL Upgrade Compatibility Tool]时可能的工作流：

![[!DNL Upgrade Compatibility Tool]关系图](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool]演示

观看此视频以了解[!DNL Upgrade Compatibility Tool]：

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## 帮助改进[!DNL Upgrade Compatibility Tool]

如果您需要本指南未涵盖的信息或疑问，请使用以下资源：

要与[!DNL Upgrade Compatibility Tool]团队联系，请通过工程Slack渠道[#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F)联系我们。 我们希望听到您的反馈、问题和建议，以帮助我们改进该工具。

[!DNL Upgrade Compatibility Tool]使用在我们的[编码标准](https://developer.adobe.com/commerce/php/coding-standards/)中定义的规则，以确保您的项目遵循Adobe Commerce最佳实践，并帮助您改进和扩展[!DNL Upgrade Compatibility Tool]。

有关提交编码标准的详细信息，请参阅[Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/)主题。

## 资源

请参阅以下资源以帮助您了解Adobe Commerce升级：

- [升级指南](../overview.md)概述了典型的Adobe Commerce升级历程以及沿途可遵循的最佳实践。
- [即将发布的版本](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/planning/schedule)页面提供了已计划和即将发布的版本的日期。
- [社区资源](https://developer.adobe.com/commerce/contributor/community/)页面用于开始讨论或查找更多信息。
- 检查[相关工具](../upgrade-compatibility-tool/related-tools.md)页面，了解典型升级历程中有用的工具。
