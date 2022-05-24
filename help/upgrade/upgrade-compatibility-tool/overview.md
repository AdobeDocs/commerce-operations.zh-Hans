---
title: 概述 [!DNL Upgrade Compatibility Tool]
description: 了解 [!DNL Upgrade Compatibility Tool] 以及它如何帮助您完成Adobe Commerce项目。
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# 指南概述

本指南面向Adobe Commerce的管理员和软件工程师。 其中包含有关安装 [!DNL Upgrade Compatibility Tool]，以及其配置和管理。 该指南假定您基本了解核心商务配置和功能。

## 概述 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

的 [!DNL Upgrade Compatibility Tool] 是一个命令行工具，可通过分析其中安装的所有模块和核心代码，根据特定版本检查Adobe Commerce自定义实例。 它会返回一个关键问题、错误和警告的列表，在升级到较新版本的Adobe Commerce之前，必须解决这些问题。

请参阅 [运行工具](../upgrade-compatibility-tool/run.md) 以了解更多信息。

请参阅 [安装](../upgrade-compatibility-tool/install.md) 的 [!DNL Upgrade Compatibility Tool].

请参阅 [视频教程](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02)以进一步了解 [!DNL Upgrade Compatibility Tool].

### 工作流

下图显示了运行 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 图表](../../assets/upgrade-guide/uct-diagram-v5.png)

### 的 [!DNL Upgrade Compatibility Tool] 用例

以下用例介绍了Adobe Commerce合作伙伴升级客户端实例的典型流程：

1. 下载 [!DNL Upgrade Compatibility Tool] 包来自Adobe Commerce存储库(`https://repo.magento.com/`)。 请参阅 [下载 [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) 主题以了解更多信息。
1. 执行 [!DNL Upgrade Compatibility Tool] 在 [β](https://devdocs.magento.com/release/beta-program.html) 最新阶段 [Adobe Commerce版本](https://devdocs.magento.com/release/).
1. 为当前安装的特定Adobe Commerce版本生成一个原版实例。 请参阅 [参与者指南](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) 有关使用 `instance` 命令生成香草安装。

   >[!NOTE]
   >
   >原版实例是特定版本的指定版本标记或分支的全新安装。

1. 的 [!DNL Upgrade Compatibility Tool] 确定将帮助软件工程师了解升级的复杂性并评估升级工作的升级问题。
1. 此信息将与利益相关方共享。
1. 将为升级定义预算和时间表。
1. 然后，软件工程师可以处理所需的代码修改以修复损坏的模块。
1. 的 [!DNL Upgrade Compatibility Tool] 可以执行以跟踪升级进度。
1. 现在，所有检出和工程部门都可以将代码推送到暂存环境，在暂存环境中，回归测试确认所有测试均为绿色，这允许他们在Adobe Commerce预发行版发布的同一天将最新的Adobe Commerce版本发布到生产环境。

   ![[!DNL Upgrade Compatibility Tool] 受众](../../assets/upgrade-guide/audience-uct-v3.png)

### 帮助改进 [!DNL Upgrade Compatibility Tool]

如果您需要信息或遇到本指南未涵盖的问题，请使用以下资源：

与 [!DNL Upgrade Compatibility Tool] 团队，通过工程Slack渠道与我们联系 [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). 我们希望听取您的反馈、问题和建议，以帮助我们改进该工具。

的 [!DNL Upgrade Compatibility Tool] 使用 [编码标准](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) 以确保您的项目遵循Adobe Commerce最佳实践，并帮助您改进和扩展 [!DNL Upgrade Compatibility Tool].

请参阅 [Contribute](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  主题以了解有关贡献编码标准的更多信息。

### 资源

我们开发了以下资源来帮助您了解Adobe Commerce升级：

- [升级指南](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [即将发行的版本](https://devdocs.magento.com/release/)
- [社区资源](https://devdocs.magento.com/community/resources/resources.html) 页面以了解更多信息。
- [相关工具](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html)
