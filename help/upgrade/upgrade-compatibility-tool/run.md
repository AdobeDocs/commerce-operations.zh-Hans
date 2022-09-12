---
title: “运行 [!DNL Upgrade Compatibility Tool]"
description: 按照以下步骤运行 [!DNL Upgrade Compatibility Tool] 在命令行界面中。Adobe Commerce项目
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 0%

---


# 下载 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

要开始使用 [!DNL Upgrade Compatibility Tool] 在命令行界面中，通过运行以下命令下载它：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

您可能需要为工具授予可执行权限，具有 `chmod` 命令：

```bash
chmod +x ./uct/bin/uct
```

## 的 [!DNL Upgrade Compatibility Tool] 在命令行界面中

的 [!DNL Upgrade Compatibility Tool] 是一个工具，可通过分析Adobe Commerce中安装的所有模块，根据特定版本检查该自定义实例。 它会返回一个关键问题、错误和警告的列表，在升级到最新版本的Adobe Commerce之前，必须解决这些问题。

请参阅 [视频教程](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02)以进一步了解 [!DNL Upgrade Compatibility Tool].

可用的命令 [!DNL Upgrade Compatibility Tool] 在命令行界面中：

| **命令** | **描述** |
|----------------|-----------------|
| `upgrade:check` | 此命令运行 [!DNL Upgrade Compatibility Tool] 分析其中安装的所有模块。 |
| `dbschema:diff` | 此命令显示两个指定的Adobe Commerce版本之间数据库架构的所有差异。 |
| `core:code:changes` | 此命令将您当前的Adobe Commerce安装与干净的香草安装进行比较。 |
| `refactor` | 此命令会自动修复一组减少的问题。 |
| `graphql:compare` | 此命令提供了用于检查两个GraphQL端点并比较其架构的选项。 |
| `list` | 此命令返回所有 [!DNL Upgrade Compatibility Tool] 中。 |
| `help` | 此命令返回所有可用 `help`选项 [!DNL Upgrade Compatibility Tool]. 此命令以及先前命令的一个选项均可运行。 |

## 使用 `upgrade:check` 命令

的 `upgrade:check` 命令会检查特定Adobe Commerce实例的核心代码更改，以及其中安装的所有自定义代码更改。

的 `upgrade:check` 命令是执行该工具的主命令：

```bash
bin/uct upgrade:check <dir>
```

其中 `<dir>` value是Adobe Commerce实例所在的目录。

可用选项 `upgrade:check` 命令：

| **命令** | **可用选项** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help:返回所有可用选项。</li><li> — 最小问题级别：您可以根据最小问题级别过滤问题（默认值为“警告”）。</li><li>—ignore-current-version-compatibility-issues（或 — i）：如果不想在报表中包含当前版本的严重问题、错误和警告。</li><li> — 即将发布的版本（或 — c）：定位特定的Adobe Commerce版本。</li></ul> |

的 [!DNL Upgrade Compatibility Tool] 允许您运行 `upgrade:check` 命令 `--ignore-current-version-compatibility-issues` 选项。 当您只想获取因更新而引入的新问题（从当前版本更新到中的目标版本）时，请使用此选项 [!DNL Upgrade Compatibility Tool] 报表：

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> 这仅适用于PHP API验证。

### 添加 `--coming-version` 选项

您可以将当前Adobe Commerce安装与任何Adobe Commerce版本进行比较 `>=2.3` 使用 `--coming-version` 选项。

运行 `upgrade:check` 命令：

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

其中 `-c, --coming-version[=COMING-VERSION]` 是指Adobe Commerce目标版本。

运行 `--coming-version`:

- 此参数是指标识特定版本Adobe Commerce的任何标记。
- 需要明确提供此内容；仅提供其值不起作用。
- 提供不带任何引号（无单引号或双引号）的标记版本： ~~“2.4.1-develop”~~.
- 您不应提供比当前安装的版本旧，也不应提供比2.3版本旧，2.3版本是当前支持的最旧版本。

## 使用 `dbschema:diff` 命令

您可以检索两个Adobe Commerce版本的数据库架构之间的差异。

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

其中参数如下所示：

- `<current-version>`:任何Adobe Commerce版本进行比较。
- `<target-version>`:以及要比较的任何Adobe Commerce版本。

执行示例：

```bash
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## 使用 `core:code:changes` 命令

您可以比较当前Adobe Commerce安装，以验证是否修改了Adobe Commerce的核心代码以实施自定义。 此命令仅显示核心修改列表：

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

其中参数如下所示：

- `<dir>`:Adobe Commerce安装目录。
- `<vanilla dir>`:Adobe Commerce香草安装目录。

可用选项 `core:code:changes` 命令：

| **命令** | **可用选项** |
|----------------|-----------------|
| `core:code:changes` | `--help`:返回所有可用 `--help` 选项。 |

>[!NOTE]
>
> 最好将自定义代码排除在核心代码之外。 请参阅Adobe Commerce 2.4 [升级指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 以了解更多升级最佳实践。

### 香草安装

A _香草_ 安装是对特定发行版本的指定版本标记或分支的全新安装。

的 `bin/uct core:code:changes` 命令会检查系统中是否存在vanilla实例。 如果这是首次使用香草版安装，则交互式命令行问题将提示您从Adobe Commerce存储库(`https://repo.magento.com/`)。

您可以运行 [!DNL Upgrade Compatibility Tool] 命令 `--vanilla-dir` 选项以指定Adobe Commerce vanilla安装目录。

请参阅 [部署原版实例](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) 主题以了解更多信息。

## 使用 `refactor` 命令

的 [!DNL Upgrade Compatibility Tool] 能够自动修复减少的一组问题：

- 允许在不传递参数的情况下使用但现在已弃用此用法的函数。
- 使用 `$this` 在Magento模板中。
- 使用PHP关键词 `final` 在专用方法中。

为此，请执行 `refactor` 命令：

```bash
bin/uct refactor <dir>
```

其中 `<dir>` value是Adobe Commerce实例所在的目录。

可用选项 `refactor` 命令：

| **命令** | **可用选项** |
|----------------|-----------------|
| `refactor` | `--help`:返回所有可用 `--help` 选项。 |

## 使用 `graphql:compare` 命令

此命令为 [!DNL Upgrade Compatibility Tool] 要检查两个GraphQL端点并比较其架构，以查找它们之间的中断和危险更改：

```bash
bin/uct graphql:compare <schema1> <schema2>
```

其中参数如下所示：

- `<schema1>`:现有安装的端点URL。
- `<schema2>`:香草安装的端点URL。

可用选项 `graphql:compare` 命令：

| **命令** | **可用选项** |
|----------------|-----------------|
| `graphql:compare` | `--help`:返回所有可用 `--help` 选项。 |

## 使用 `list` 命令

返回 [!DNL Upgrade Compatibility Tool] 可用命令，运行：

```bash
bin/uct list
```

## 使用 `--help` 命令

要查看 [!DNL Upgrade Compatibility Tool] 命令常规选项和帮助，运行：

```bash
bin/uct --help
```

这会返回一个包含所有可用项的列表 `help` 选项 [!DNL Upgrade Compatibility Tool] 在命令行界面中：

```terminal
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

但是，可以运行 `--help` 作为选项。 这将返回特定 `--help` 选项。

示例 `upgrade:check` 命令 `--help` 选项：

```bash
bin/uct upgrade:check --help
```

这会返回可为 `upgrade:check` 命令：

```terminal
--min-issue-level.
-i, --ignore-current-version-compatibility-issues.
```

## 遵循Adobe Commerce最佳实践

- 请避免使用两个同名模块。
- 关注Adobe Commerce [编码标准](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [升级指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 最佳实践。

## 优化结果

的 [!DNL Upgrade Compatibility Tool] 提供包含结果的报表，其中默认包含项目中发现的所有问题。 您可以优化结果以重点关注完成升级所必须修复的问题：

- 使用选项 `--ignore-current-version-compatibility-issues` 当您只想获取随更新而引入的新问题(从您的当前版本更新到 [!DNL Upgrade Compatibility Tool] 报表。
- 添加 `--min-issue-level` 选项，此设置允许设置最小问题级别，以帮助只排定升级中最重要问题的优先级。
- 的 [!DNL Upgrade Compatibility Tool] 需要至少2GB的RAM才能运行。 建议使用此设置以避免由于内存不足而出现的问题。 的 [!DNL Upgrade Compatibility Tool] 如果运行 `upgrade:check` 命令 `memory_limit` 设置。
