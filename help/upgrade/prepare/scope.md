---
title: 了解升级范围
description: 了解在发行版中向后进行不兼容的更改，这些更改可能会影响Adobe Commerce、Magento Open Source自定义模块或第三方扩展。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 了解升级范围

查看 [发行说明](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) 以了解版本的范围，包括增强功能、错误修复以及可能影响第三方和自定义模块的已知问题。

## 后向不兼容的更改

Adobe Commerce和Magento Open Source版本可能包含不兼容的后向更改。 请查看我们的后向不兼容更改文档，请参阅以下内容：

- **[主要变化亮点](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)** — 具有重大影响的更改，需要详细说明和特殊说明以确保第三方模块继续工作。
- **[次要更改引用](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)** — 从代码库生成的引用文档，该文档描述对类、API成员资格、数据库、依赖项注入、接口、布局、系统和XSD的细微更改。

## 第三方扩展

Adobe Commerce Marketplace的新兼容性政策确保 _全部_ 列出的扩展在GA日期后30天内与最新发布的版本兼容。 因此，必须尽可能通过Marketplace获取第三方扩展。

## 自定义模块

应针对您要升级到的目标版本检查所有自定义模块。 这是升级过程中最耗时、最耗资的过程。 在评估自定义模块时，您必须查找向后不兼容的更改，并了解一些新实践，如控制器分解。 您可以在 [发行说明](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). 另外，请确保 [最佳实践](https://devdocs.magento.com/guides/v2.4/ext-best-practices/extension-coding/common-programming-bp.html) 用于模块开发。

## 升级兼容性工具

升级兼容性工具是一个命令行工具，可分析您的实例以发现潜在的升级问题。 它会检查您安装的当前版本与您尝试升级到的版本之间是否存在问题。

使用此工具可减少团队了解升级范围和影响所需的工作量。 它有助于您避免在升级时出现的常见代码问题，并就如何解决已识别的问题提供明确的指导。 它还有助于优先处理确保成功升级所需的最关键问题，从而在升级时节省时间和成本。

请参阅以下部分以开始使用升级兼容性工具。 请参阅升级兼容性工具 [指南](../upgrade-compatibility-tool/overview.md) 以了解更多技术详细信息和高级用例。

### 下载工具

使用编辑器下载工具。 它需要PHP 7.3或更高版本、至少2GB的RAM、Node.js（如果您正在检查GraphQL兼容性）以及Adobe Commerce许可证。

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
> 的 `<dir>` 参数是存储代码库的目录。 的 `-c` 选项会将您的代码库与指定的版本（例如，2.4.4）进行比较。

要确定团队要解决的最关键问题，请执行以下操作：

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

要与此命令一起使用的其他选项有：

- `--ignore-current-version-compatibility-issues` — 禁止针对当前版本的所有已知严重问题、错误和警告。 它仅针对您尝试升级的版本提供错误。

- `--min-issue-level` — 允许您设置最小问题级别，以帮助仅排定升级中最重要问题的优先级。 选项以严重性的升序顺序显示警告、错误和严重。

- `-m | [=MODULE-PATH]` — 如果只想分析某个供应商、模块甚至目录，则还可以指定路径作为选项。

- `--vanilla-dir` — 允许您检查核心代码，以了解任何非标准功能或自定义实施。 必须事先清理。 系统会自动下载您版本的香草实例以供参考。

   >[!NOTE]
   >
   > 这也可以通过 `core:code:changes` 命令)。

### 分析输出

升级兼容性工具会导出一个JSON文件，以标识受影响的代码或模块、严重性以及它遇到的每个问题的问题描述。 它还会输出包含复杂性分数的摘要报表，以便您的团队大致了解升级到最新版本所需的操作。 复杂性分数越低，执行升级就越容易。

以下输出显示了摘要报表示例：

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

已识别工具的所有问题都会列在报表中，并带有特定的错误代码。 使用 [错误消息引用](../upgrade-compatibility-tool/error-messages.md) 以获取有关每个问题的更多详细信息。 Adobe还提供了修复每个问题类型的建议，以便您可以规划修正步骤。

使用此报表可估算更新升级代码所需的工作量。 根据您的经验，您可以根据已识别的问题总数和问题的严重性，估计升级所需的工作量。 由于这是一个命令行工具，因此您可以将它合并到自动测试和代码检查包中，并使用JSON输出来生成报表。

我们建议保存每个升级项目的结果，以便您能够将将来的升级结果与以前的结果进行比较。 通过持续使用，您将开始充分了解从工具提供的摘要报告升级到下一版本需要付出的工作量。

我们还建议您在进行升级时定期运行该工具，以便查看您的进度。 问题数应在您修复时减少。 这还有助于您的团队确定分发工作的最佳方法。

该工具的未来版本将包含PHP 8.1兼容性测试和自动修复，以帮助您尽快修复问题。
