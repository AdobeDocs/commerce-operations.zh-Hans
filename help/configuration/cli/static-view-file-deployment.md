---
title: 部署静态视图文件
description: 了解如何在生产模式期间将静态文件写入Commerce文件系统。
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: 0a72bc492dfec0a9014a518282a97ab21e59f96d
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# 部署静态视图文件

{{file-system-owner}}

使用static view files deployment命令，您可以在设置Commerce软件时，将静态文件写入Commerce文件系统 [生产模式](../bootstrap/application-modes.md#production-mode).

术语 _静态视图文件_ 是指以下内容：

- “静态”表示可以为站点缓存它（即，文件不是动态生成的）。 示例包括从LESS生成的图像和CSS。
- “视图”是指表示层（来自MVC）。

静态视图文件位于 `<magento_root>/pub/static` 目录，并且某些文件缓存在 `<magento_root>/var/view_preprocessed` 目录。

静态视图文件部署受以下应用程序模式影响：

- [默认](../bootstrap/application-modes.md#default-mode) 和 [开发人员](../bootstrap/application-modes.md#developer-mode) 模式：Commerce会根据需要生成模式，但其余模式将缓存在文件中，以提高访问速度。
- [生产](../bootstrap/application-modes.md#production-mode) 模式：静态文件为 _非_ 生成或缓存。

您必须使用本主题中介绍的命令手动将静态视图文件写入Commerce文件系统；之后，您可以限制权限以限制漏洞并防止意外或恶意覆盖文件。

>[!WARNING]
>
>_仅开发人员模式_：安装或启用新模块时，它可能会加载新的JavaScript、CSS、布局等。 要避免出现静态文件问题，您必须清除旧文件，以确保您获得新模块的所有更改。 您可以通过多种方式清理生成的静态视图文件。 请参阅 [清理静态文件缓存主题以了解详细信息](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) 以了解更多信息。

**部署静态视图文件**：

1. 以或身份登录Commerce服务器 [切换到文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 删除内容 `<magento_root>/pub/static`，但以下各项除外 `.htaccess` 文件。 请勿删除此文件。
1. 运行静态视图文件部署工具 `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >如果在Admin中启用静态视图文件合并，则 `pub/static` 目录系统必须是可写的。

   命令选项：

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

下表说明了此命令的参数和值。

| 选项 | 描述 | 必需？ |
| ------ | ----------- | --------- |
| `<languages>` | 以空格分隔的列表 [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) 要输出静态视图文件的语言代码。 (默认为 `en_US`.)<br>通过运行以下命令查找列表： `bin/magento info:language:list` | 否 |
| `--language (-l)` | 仅生成指定语言的文件。 缺省情况下，不指定任何选项，生成所有ISO-639语言代码的文件。 您可以一次指定一个语言代码的名称。 默认值为 **所有**.<br>例如： `--language en_US --language es_ES` | 否 |
| `--exclude-language` | 为指定的语言代码生成文件。 默认情况下，未指定任何选项，即不排除任何内容。 您可以指定一个语言代码的名称，也可以指定以逗号分隔的语言代码列表。 默认值为 **无**. | 否 |
| `--theme <theme>` | 要部署静态内容的主题。 默认值为 **所有**.<br>例如： `--theme Magento/blank --theme Magento/luma` | 否 |
| `--exclude-theme <theme>` | 部署静态内容时要排除的主题。 默认值为 **无**.<br>例如， `--exclude-theme Magento/blank` | 否 |
| `--area (-a)` | 仅为指定区域生成文件。 缺省情况下，未指定选项，将为所有区域生成文件。 有效值为 `adminhtml` 和 `frontend`. 默认值为 **所有**.<br>例如： `--area adminhtml` | 否 |
| `--exclude-area` | 不要为指定区域生成文件。 默认情况下，未指定任何选项，即不排除任何内容。 默认值为 **无**. | 否 |
| `--jobs (-j)` | 启用 [并行处理](manage-indexers.md#reindexing-in-parallel-mode) 使用指定数量的作业。 缺省值为0 （不在并行进程中运行）。 默认值为 **0**. | 否 |
| `--symlink-locale` | 为这些区域设置的文件创建符号链接，这些区域设置传递用于部署，但没有进行自定义。 | 否 |
| `--content-version=CONTENT-VERSION` | 如果在多个节点上运行部署，可以使用静态内容的自定义版本，以确保静态内容版本相同且缓存正常工作。 | 否 |
| `--no-javascript` | 不部署JavaScript文件 | 否 |
| `--no-css` | 不部署CSS文件。 | 否 |
| `--no-less` | 请勿部署LESS文件。 | 否 |
| `--no-images` | 不部署映像。 | 否 |
| `--no-fonts` | 不部署字体文件。 | 否 |
| `--no-html` | 不部署HTML文件。 | 否 |
| `--no-misc` | 请勿部署其他类型的文件：MD、JBF、CSV、JSON、TXT、HTC、SWF | 否 |
| `--no-html-minify` | 请勿缩小HTML文件。 | 否 |
| `-s <quick\|standard\|compact>` | 定义部署策略。 仅当有多个本地时，才使用这些选项。<ul><li>使用 [快速策略](static-view-file-strategy.md#quick-strategy) 以最大限度地缩短部署时间。 如果未指定，则这是缺省命令选项。</li><li>使用 [标准策略](static-view-file-strategy.md#standard-strategy) 以部署所有包的所有静态视图文件。</li><li>使用 [压缩策略](static-view-file-strategy.md#compact-strategy) 以节省服务器上的磁盘空间。</li></ul> | 否 |
| `--no-parent` | 不为当前主题的父主题生成文件。 如果您未明确使用尝试部署的当前主题的父主题，强烈建议您使用此标记。 这显着提高了该过程的速度。 此标记在Commerce 2.4.2中可用 | 否 |
| `--force (-f)` | 以任何模式部署文件。 (默认情况下，静态内容部署工具只能在生产模式下运行。 使用此选项可在默认或开发人员模式下运行它)。 | 否 |

>[!INFO]
>
>如果同时指定这两个值 `<languages>` 和 `--language`， `<languages>` 优先。

## 示例

以下是一些示例命令。

### 排除主题和HTML缩小

以下命令为美式英语部署静态内容(`en_US`)语言，不包括随Commerce提供的Luma主题，并且不会缩小HTML文件。

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

以下命令使用标准部署策略仅部署JavaScript，其中4个作业：

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

以下命令仅部署CSS和LESS，包含3个作业和一个快速部署策略：

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### 为一个主题和一个区域生成静态视图文件

以下命令为所有语言生成静态视图文件，仅前端区域，仅Commerce Luma主题，不生成字体：

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

## 在不安装Commerce的情况下部署静态视图文件

您可能希望在单独的非生产环境中运行部署过程，以避免在敏感的生产计算机上执行任何构建过程。

为此，请执行以下步骤：

1. 运行 [`bin/magento app:config:dump`](../cli/export-configuration.md) 以从生产系统导出配置。
1. 将导出的文件复制到非生产代码库。
1. 部署静态视图文件： `bin/magento setup:static-content:deploy`

## 静态视图文件部署工具疑难解答

[首先安装Commerce软件](../../installation/overview.md)；否则，将无法运行静态视图文件部署工具。

**症状**：运行静态视图文件部署工具时，会显示以下错误：

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**解决方案**：

请使用以下步骤：

1. 使用安装Commerce软件 [命令行](../../installation/composer.md).
1. 以或身份登录到应用程序服务器 [切换到](../../installation/prerequisites/file-system/overview.md)，即文件系统所有者。
1. 删除内容 `<app_root>/pub/static` 目录，但 `.htaccess` 文件。 请勿删除此文件。
1. 部署静态视图文件： `bin/magento setup:static-content:deploy`

## 开发人员自定义静态内容部署工具的提示

创建静态内容部署工具的自定义实施时，请仅使用原子文件写入来写入应在客户端上可用的文件。 如果使用非原子文件写入，则这些文件可能会加载到包含部分内容的客户端上。

使其成为原子文件的选项之一是，写入存储在临时目录中的文件，并在写入结束后将其复制或移动到目标目录（从目标目录将其加载到客户端）。 有关写入文件的详细信息，请参见 [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
