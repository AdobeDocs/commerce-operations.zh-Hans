---
title: 部署静态视图文件
description: 了解如何在生产模式期间将静态文件写入商务文件系统。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 0%

---


# 部署静态视图文件

{{file-system-owner}}

使用静态视图文件部署命令可以写入 [静态文件](https://glossary.magento.com/static-files) 当为 [生产模式](../bootstrap/application-modes.md#production-mode).

术语 _静态视图文件_ 是指：

- “静态”表示它可以缓存给站点（即文件不是动态生成的）。 示例包括从LESS生成的图像和CSS。
- “视图”是指表示层（从MVC）。

静态视图文件位于 `<magento_root>/pub/static` 目录中，并且有些缓存在 `<magento_root>/var/view_preprocessed` 目录。

静态视图文件部署受应用程序模式的影响，如下所示：

- [默认](../bootstrap/application-modes.md#default-mode) 和 [开发人员](../bootstrap/application-modes.md#developer-mode) 模式：商务会根据需要生成这些文件，但其余文件会缓存在文件中，以提高访问速度。
- [生产](../bootstrap/application-modes.md#production-mode) 模式：静态文件为 _not_ 生成或缓存。

您必须使用本主题中讨论的命令手动将静态视图文件写入商务文件系统；之后，您可以限制权限以限制您的漏洞，并防止文件意外或恶意覆盖。

>[!WARNING]
>
>_仅限开发人员模式_:安装或启用新模块时，可能会加载新的JavaScript、CSS、布局等。 要避免静态文件出现问题，您必须清理旧文件，以确保获取新模块的所有更改。 您可以通过多种方式清理生成的静态视图文件。 请参阅 [清除静态文件缓存主题以了解详细信息](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/cache_for_frontdevs.html#clean_static_cache) 以了解更多信息。

**部署静态视图文件**:

1. 以或的形式登录到商务服务器 [切换到文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 删除 `<magento_root>/pub/static`，但 `.htaccess` 文件。 请勿删除此文件。
1. 运行静态视图文件部署工具 `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >如果在“管理员”中启用静态视图文件合并，则 `pub/static` 目录系统必须可写。

   命令选项：

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

下表说明了此命令的参数和值。

| 选项 | 描述 | 必需？ |
| ------ | ----------- | --------- |
| `<languages>` | 空格分隔列表 [ISO-639](http://www.loc.gov/standards/iso639-2/php/code_list.php) 要输出静态视图文件的语言代码。 (默认值为 `en_US`.)<br>通过运行以查找列表： `bin/magento info:language:list` | 否 |
| `--language (-l)` | 仅为指定语言生成文件。 缺省设置（未指定选项）是为所有ISO-639语言代码生成文件。 您一次可以指定一个语言代码的名称。 默认值为 **全部**.<br>例如： `--language en_US --language es_ES` | 否 |
| `--exclude-language` | 为指定的语言代码生成文件。 未指定任何选项的默认值是不排除任何内容。 您可以指定一种语言代码的名称或以逗号分隔的语言代码列表。 默认值为 **无**. | 否 |
| `--theme <theme>` | 用于部署静态内容的主页。 默认值为 **全部**.<br>例如： `--theme Magento/blank --theme Magento/luma` | 否 |
| `--exclude-theme <theme>` | 部署静态内容时要排除的主题。 默认值为 **无**.<br>例如，`--exclude-theme Magento/blank` | 否 |
| `--area (-a)` | 仅为指定区域生成文件。 默认值（未指定选项）是为所有区域生成文件。 有效值为 `adminhtml` 和 `frontend`. 默认值为 **全部**.<br>例如： `--area adminhtml` | 否 |
| `--exclude-area` | 请勿为指定区域生成文件。 未指定任何选项的默认值是不排除任何内容。 默认值为 **无**. | 否 |
| `--jobs (-j)` | 使用指定数量的作业启用并行处理。 默认值为0（不在并行进程中运行）。 默认值为 **0**. | 否 |
| `--symlink-locale` | 为这些区域设置的文件创建符号链接，这些文件将传递用于部署，但没有自定义设置。 | 否 |
| `--content-version=CONTENT-VERSION` | 如果在多个节点上运行部署，则可以使用静态内容的自定义版本，以确保静态内容版本相同且缓存工作正常。 | 否 |
| `--no-javascript` | 不部署JavaScript文件 | 否 |
| `--no-css` | 请勿部署CSS文件。 | 否 |
| `--no-less` | 请勿部署LESS文件。 | 否 |
| `--no-images` | 请勿部署图像。 | 否 |
| `--no-fonts` | 请勿部署字体文件。 | 否 |
| `--no-html` | 请勿部署HTML文件。 | 否 |
| `--no-misc` | 请勿部署其他类型的文件：MD、JBF、CSV、JSON、TXT、HTC、SWF | 否 |
| `--no-html-minify` | 请勿缩小HTML文件。 | 否 |
| `-s <quick\|standard\|compact>` | 定义部署策略。 仅当您有多个本地选项时，才使用这些选项。<ul><li>使用 [快速策略](static-view-file-strategy.md#quick-strategy) 以最大程度地缩短部署时间。 如果未指定，这是缺省命令选项。</li><li>使用 [标准策略](static-view-file-strategy.md#standard-strategy) 为所有包部署所有静态视图文件。</li><li>使用 [紧凑策略](static-view-file-strategy.md#compact-strategy) 以节省服务器上的磁盘空间。</li></ul> | 否 |
| `--no-parent` | 请勿为当前主题的父主题生成文件。 如果您未明确使用尝试部署的当前主题的父主题，则强烈建议使用此标记。 这会显着提高处理速度。 此标记在Commerce 2.4.2中可用 | 否 |
| `--force (-f)` | 以任何模式部署文件。 (默认情况下，静态内容部署工具只能在生产模式下运行。 使用此选项可在默认或开发人员模式下运行它)。 | 否 |

>[!INFO]
>
>如果同时为两者指定值 `<languages>` 和 `--language`, `<languages>` 优先。

## 示例

以下是一些示例命令。

### 排除主题和HTML缩小

以下命令为美国英语部署静态内容(`en_US`)语言，不包括随Commerce提供的Luma主题，且不会缩小HTML文件。

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

示例输出：

```terminal
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

以下命令仅部署具有标准部署策略的JavaScript（包含4个作业）：

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

以下命令仅部署具有3个作业的CSS和LESS，并且还部署了快速部署策略：

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### 为一个主题和一个区域生成静态视图文件

以下命令为所有语言（仅前端区域）生成静态视图文件，仅Commerce Luma主题，而不生成字体：

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

示例输出：

```terminal
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## 无需安装Commerce即可部署静态视图文件

您可能希望在单独的非生产环境中运行部署过程，以避免在敏感的生产计算机上执行任何构建过程。

为此，请执行以下步骤：

1. 运行 [`bin/magento app:config:dump`](../cli/export-configuration.md) 从生产系统导出配置。
1. 将导出的文件复制到非生产代码库。
1. 部署静态视图文件： `bin/magento setup:static-content:deploy`

## 静态视图文件部署工具故障诊断

[首先安装商务软件](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html);否则，将无法运行静态视图文件部署工具。

**症状**:运行静态视图文件部署工具时，会显示以下错误：

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**解决方案**:

请执行以下步骤：

1. 使用 [命令行](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli.html).
1. 以或的形式登录到商务服务器 [切换到](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)，文件系统所有者。
1. 删除 `<magento_root>/pub/static` 目录，但 `.htaccess` 文件。 请勿删除此文件。
1. 部署静态视图文件： `bin/magento setup:static-content:deploy`

## 面向开发人员的自定义静态内容部署工具提示

在创建静态内容部署工具的自定义实施时，请仅对客户端上应该可用的文件使用原子文件写入。 如果您使用非原子文件写入，则这些文件可能会加载到客户端上，并包含部分内容。

使其具有原子性的选项之一是，写入临时目录中存储的文件，并在写入结束后将其复制或移动到目标目录（从其处加载到客户端）。 有关写入文件的详细信息，请参阅 [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
