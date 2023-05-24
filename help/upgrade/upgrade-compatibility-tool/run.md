---
title: 运行 [!DNL Upgrade Compatibility Tool]
description: 按照以下步骤运行 [!DNL Upgrade Compatibility Tool] 在Adobe Commerce项目的命令行界面中。
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 0%

---

# 下载 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

要开始使用 [!DNL Upgrade Compatibility Tool] 在命令行界面中，通过运行以下命令下载它：

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

您可能需要为工具的可执行文件授予 `chmod` 命令：

```bash
chmod +x ./uct/bin/uct
```

## 此 [!DNL Upgrade Compatibility Tool] 在命令行界面中

此 [!DNL Upgrade Compatibility Tool] 是一种工具，用于通过分析安装在Adobe Commerce自定义实例中的所有模块，根据特定版本检查该实例。 它会返回在升级到最新版本的Adobe Commerce之前必须解决的严重问题、错误和警告列表。

查看此 [视频教程](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02)了解关于 [!DNL Upgrade Compatibility Tool].

可用的命令 [!DNL Upgrade Compatibility Tool] 在命令行界面中：

| **命令** | **描述** |
|----------------|-----------------|
| `upgrade:check` | 此命令运行 [!DNL Upgrade Compatibility Tool] 分析其中安装的所有模块。 |
| `dbschema:diff` | 此命令显示两个指定的Adobe Commerce版本之间数据库架构的所有差异。 |
| `core:code:changes` | 此命令会将您当前的Adobe Commerce安装与干净的vanilla安装进行比较。 |
| `refactor` | 此命令会自动修复一组减少的问题。 |
| `graphql:compare` | 此命令提供选项，用于内检两个GraphQL端点并比较其架构。 |
| `list` | 此命令返回所有 [!DNL Upgrade Compatibility Tool] 可用命令。 |
| `help` | 此命令返回所有可用的 `help`的选项 [!DNL Upgrade Compatibility Tool]. 此命令可以与前面的命令一起运行。 |

## 使用 `upgrade:check` 命令

此 `upgrade:check` 命令会检查该特定Adobe Commerce实例的核心代码更改以及其中安装的所有自定义代码更改。

此 `upgrade:check` command是执行该工具的主命令：

```bash
bin/uct upgrade:check <dir>
```

位置 `<dir>` value是Adobe Commerce实例所在的目录。

的可用选项 `upgrade:check` 命令：

| **命令** | **可用选项** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help：返回所有可用选项。</li><li>—current-version：当前的Adobe Commerce版本。 此参数是必需的，必须始终使用。</li><li>—min-issue-level：您可以根据最小问题级别筛选问题（默认值为WARNING）。</li><li>—ignore-current-version-compatibility-issues（或 — i）：如果您不想在报表中包含来自当前版本的严重问题、错误和警告。</li><li> — 即将推出的版本（或 — c）：定位特定的Adobe Commerce版本。 如果省略，将使用最新可用的。</li></ul> |

此 [!DNL Upgrade Compatibility Tool] 允许您运行 `upgrade:check` 命令和 `--ignore-current-version-compatibility-issues` 选项。 当您只想获取更新时引入的新问题，从当前版本更新到中的目标版本时，可使用此选项 [!DNL Upgrade Compatibility Tool] 报告：

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> 这仅适用于PHP API验证。

### 添加 `--coming-version` option

您可以将当前Adobe Commerce安装与任何Adobe Commerce版本进行比较 `>=2.3` 通过使用 `--coming-version` 选项。

在运行 `upgrade:check` 命令：

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

位置 `-c, --coming-version[=COMING-VERSION]` 指Adobe Commerce目标版本。

运行有一些限制 `--coming-version`：

- 此参数是指标识特定Adobe Commerce版本的任何标记。
- 需要明确提供此值；仅提供其值不起作用。
- 提供不带任何引号的标记版本（无论是单引号还是双引号）： ~~&#39;2.4.1 — 开发&#39;~~.
- 您不应提供比当前安装的版本更旧的版本，也不应提供比2.3更旧的版本（这是当前支持的最旧的版本）。

## 使用 `dbschema:diff` 命令

您可以检索两个Adobe Commerce版本的数据库架构之间的差异。

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

其中参数如下：

- `<current-version>`：用于比较的任何Adobe Commerce版本。
- `<target-version>`：以及任何Adobe Commerce版本进行比较。

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

您可以比较当前的Adobe Commerce安装，以验证Adobe Commerce的核心代码是否已修改以实现自定义。 此命令仅显示核心修改的列表：

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

其中参数如下：

- `<dir>`：Adobe Commerce安装目录。
- `<vanilla dir>`：Adobe Commerce vanilla安装目录。

的可用选项 `core:code:changes` 命令：

| **命令** | **可用选项** |
|----------------|-----------------|
| `core:code:changes` | `--help`：返回所有可用项 `--help` 选项。 |

>[!NOTE]
>
> 最佳做法是将自定义代码排除在核心代码之外。 请参阅Adobe Commerce 2.4 [升级指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 了解更多升级最佳实践。

### Vanilla安装

A _香草_ 安装是对特定发行版本的指定版本标记或分支的干净安装。

此 `bin/uct core:code:changes` 命令检查系统中是否存在vanilla实例。 如果这是第一次使用vanilla安装，则会出现一个交互式命令行问题，提示您从Adobe Commerce存储库下载vanilla项目(`https://repo.magento.com/`)。

您可以运行 [!DNL Upgrade Compatibility Tool] 命令和 `--vanilla-dir` 选项来指定Adobe Commerce vanilla安装目录。

请参阅 [部署vanilla实例](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) 主题以了解更多信息。

## 使用 `refactor` 命令

此 [!DNL Upgrade Compatibility Tool] 能够自动修复一组减少的问题：

- 允许在不传递参数的情况下使用，但现在已弃用此类用法的函数。
- 使用情况 `$this` 在Magento模板中。
- PHP关键字的用法 `final` 在私有方法中。

为此，请执行 `refactor` 命令：

```bash
bin/uct refactor <dir>
```

位置 `<dir>` value是Adobe Commerce实例所在的目录。

的可用选项 `refactor` 命令：

| **命令** | **可用选项** |
|----------------|-----------------|
| `refactor` | `--help`：返回所有可用项 `--help` 选项。 |

## 使用 `graphql:compare` 命令

此命令将选项提供给 [!DNL Upgrade Compatibility Tool] 要检查两个GraphQL端点并比较其架构，以找出它们之间的突破性变化和危险变化，请执行以下操作：

```bash
bin/uct graphql:compare <schema1> <schema2>
```

其中参数如下：

- `<schema1>`：现有安装的端点URL。
- `<schema2>`：Vanilla安装的端点URL。

的可用选项 `graphql:compare` 命令：

| **命令** | **可用选项** |
|----------------|-----------------|
| `graphql:compare` | `--help`：返回所有可用项 `--help` 选项。 |

## 使用 `list` 命令

要返回 [!DNL Upgrade Compatibility Tool] 可用命令，运行：

```bash
bin/uct list
```

## 使用 `help` 命令

要查看 [!DNL Upgrade Compatibility Tool] 命令常规选项和帮助，运行：

```bash
bin/uct --help
```

这将返回一个包含所有可用内容的列表 `help` 的选项 [!DNL Upgrade Compatibility Tool] 在命令行界面中：

```terminal
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

可以运行 `--help` 作为运行特定命令时的选项。 它会返回 `--help` 指定命令的选项。

示例 `upgrade:check` 命令 `--help` 选项：

```bash
bin/uct upgrade:check --help
```

这会返回可以为其运行的特定选项 `upgrade:check` 命令：

```terminal
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## 遵循Adobe Commerce最佳实践

- 避免使用具有相同名称的两个模块。
- 关注Adobe Commerce [编码标准](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [升级指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) 最佳实践。
- 运行 [!DNL Upgrade Compatibility Tool] 从 [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) 对象 [云基础架构上的Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} 个项目。

## 优化结果

此 [!DNL Upgrade Compatibility Tool] 提供包含结果的报告，其中显示项目中默认识别的所有问题。 您可以优化结果以重点关注完成升级所必须修复的问题：

- 使用选项 `--ignore-current-version-compatibility-issues` 当您只想获取更新时的新问题，这些问题会在您的中从当前版本更新到目标版本时引入 [!DNL Upgrade Compatibility Tool] 报告。
- 添加 `--min-issue-level` 选项，此设置允许设置最低问题级别，以帮助仅优先考虑升级中的最重要的问题。
- 此 [!DNL Upgrade Compatibility Tool] 至少需要2GB RAM才能运行。 建议使用此设置以避免由于内存不足限制导致的问题。 此 [!DNL Upgrade Compatibility Tool] 在运行 `upgrade:check` 命令和低 `memory_limit` 设置。
