---
title: 了解升级范围
description: 了解版本中可能影响Adobe Commerce自定义模块或第三方扩展的向后不兼容更改。
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# 了解升级的范围

查看[发行说明](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview)了解发行范围，包括增强功能、错误修复以及可能影响第三方和自定义模块的已知问题。

## 向后不兼容的更改

Adobe Commerce版本可能包含与向后不兼容的更改。 请查看我们向后不兼容的更改文档，请参阅以下内容：

- **[主要更改亮点](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/)** — 具有主要影响并需要详细说明和特殊说明以确保第三方模块继续工作的更改。
- **[次要更改引用](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)** — 引用从代码库生成的文档，其中介绍了对类、API成员资格、数据库、依赖项注入、接口、布局、系统和XSD的次要更改。

## 第三方扩展

Adobe Commerce Marketplace的新兼容性策略可确保&#x200B;_所有_&#x200B;列出的扩展与GA日期起30天内的最新发行版本兼容。 因此，请务必尽可能通过Marketplace获取第三方扩展。

## 自定义模块

所有自定义模块都应针对您要升级到的目标版本进行检查。 这是最耗时、最耗资源的升级过程。 在评估自定义模块时，必须查找与向后不兼容的更改并了解新实践，如控制器分解。 您可以在[发行说明](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview)中了解有关此内容的更多信息。 此外，请确保遵循模块开发的[最佳实践](https://developer.adobe.com/commerce/php/best-practices/extensions/)。

## [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool]是一个命令行工具，用于分析实例是否存在潜在升级问题。 它检查您安装的当前版本与尝试升级到的版本之间是否存在问题。

使用此工具可减少团队了解升级范围和影响所需的工作量。 它有助于在升级时避免出现常见的代码问题，并提供了有关如何解决已识别问题的明确指导。 它还有助于优先处理最关键的问题，以确保成功升级，从而节省升级时的时间和成本。

请参阅以下部分以开始使用[!DNL Upgrade Compatibility Tool]。 有关更多技术细节和高级用例，请参阅[!DNL Upgrade Compatibility Tool] [指南](../upgrade-compatibility-tool/overview.md)。

### 下载工具

使用Composer下载工具。 它需要PHP 7.3或更高版本、至少2 GB的RAM、Node.js(如果您正在检查GraphQL兼容性)以及Adobe Commerce许可证。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### 运行工具

要分析实例并检查错误、警告和严重问题，请执行以下操作：

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> `<dir>`参数是存储代码库的目录。 `-c`选项将您的代码库与指定的版本进行比较。

确定团队需要解决的最关键问题：

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

可以与此命令一起使用的其他选项包括：

- `--ignore-current-version-compatibility-issues` — 隐藏当前版本的所有已知严重问题、错误和警告。 它仅提供您尝试升级的版本存在的错误。

- `--min-issue-level` — 允许您设置最低问题级别，以帮助仅优先考虑升级中的最重要问题。 这些选项包括警告、错误和严重性升序严重。

- `-m | [=MODULE-PATH]` — 如果只想分析某个供应商、模块甚至目录，也可以将路径指定为选项。

- `--vanilla-dir` — 允许您检查核心代码中是否有任何非标准功能或自定义的实现。 这些东西一定要事先清理干净。 系统会自动下载您版本的vanilla实例以供参考。

  >[!NOTE]
  >
  > 这也可以使用工具中的`core:code:changes`命令来完成)。

### 分析输出

[!DNL Upgrade Compatibility Tool]导出一个JSON文件，该文件识别受影响的代码或模块、严重性以及它遇到的每个问题的描述。 它还输出带有复杂性分数的摘要报告，这使您的团队能够大致了解升级到最新版本需要执行的操作。 复杂性分数越低，执行升级就越容易。

以下输出显示了一个摘要报告示例：

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### 提示和建议

报告中列出了该工具发现的所有问题，并带有特定的错误代码。 使用[错误消息引用](../upgrade-compatibility-tool/error-messages.md)获取有关每个问题的更多详细信息。 Adobe还提供了修复每种问题类型的建议，以便您能够规划修正步骤。

使用该报表可估计更新升级代码所需的工作量。 根据您的经验，您可以根据已识别的问题总数和问题的严重性来估计升级所需的工作。 由于这是命令行工具，因此您可以将其合并到自动测试和代码检查包中，并使用JSON输出生成报告。

我们建议保存每个升级项目的结果，以便您可以将未来的升级结果与之前的结果进行比较。 通过继续使用，您将会开始充分了解仅从该工具提供的摘要报告中，升级到下一个版本所需花费的工作量。

我们还建议您在升级过程中定期运行该工具，以便了解进度。 问题的数量应随着您的修复而减少。 这还可以帮助您的团队决定分发工作的最佳方法。

[!DNL Upgrade Compatibility Tool]将继续改进，并且未来版本将包括自动修复等功能，以帮助您尽快修复问题。 2022年1月发布的最新改进包括PHP 8.1兼容性测试和HTML可视化功能，可帮助您快速识别可能需要更多升级工作的领域。
