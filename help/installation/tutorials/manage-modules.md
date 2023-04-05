---
title: 启用或禁用模块
description: 按照以下步骤管理Adobe Commerce或Magento Open Source模块。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# 启用或禁用模块

此命令没有先决条件。

## 模块状态

使用以下命令列出已启用和已禁用的模块：

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

其中

* `--enabled` 列出所有已启用的模块。
* `--disabled` 列出所有禁用的模块。
* `<module-list>` 是用于检查状态的以空格分隔的模块列表。 如果任何模块名称包含特殊字符，请用单引号或双引号引住该名称。

## 模块启用、禁用

要启用或禁用可用模块，请使用以下命令：

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

其中

* `<module-list>` 是要启用或禁用的模块列表，以空格分隔。 如果任何模块名称包含特殊字符，请用单引号或双引号引住该名称。
* `--all` 可同时启用或禁用所有模块。
* `-f` 或 `--force` 强制启用或禁用模块（尽管存在依赖关系）。 在使用此选项之前，请参阅 [关于启用和禁用模块](#about-enabling-and-disabling-modules).
* `-c` 或 `--clear-static-content` 清理 [生成的静态视图文件](../../configuration/cli/static-view-file-deployment.md).

   如果存在多个同名文件，并且您未清除所有这些文件，则无法清除静态视图文件可能会导致问题。

   换句话说，因为 [静态文件回退](../../configuration/cli/static-view-file-deployment.md) 规则，如果您未清除静态文件，并且有多个文件名为 `logo.svg` 不同，回退可能会导致显示错误的文件。

例如，要禁用 `Magento_Weee` 模块，输入：

```bash
bin/magento module:disable Magento_Weee
```

有关启用和禁用模块的重要信息，请参阅 [关于启用和禁用模块](#about-enabling-and-disabling-modules).

## 更新数据库

如果启用了一个或多个模块，请运行以下命令以更新数据库：

```bash
bin/magento setup:upgrade
```

然后清除缓存：

```bash
bin/magento cache:clean
```

## 关于启用和禁用模块

Adobe Commerce和Magento Open Source允许您启用或禁用当前可用的模块；换言之，任何Adobe提供的模块或当前可用的任何第三方模块。

某些模块对其他模块具有依赖关系，在这种情况下，您可能无法启用或禁用某个模块，因为它依赖于其他模块。

此外， *冲突* 不能同时启用的模块。

示例：

* 模块A取决于模块B。除非先禁用模块A，否则无法禁用模块B。

* 模块A取决于模块B，这两个模块均被禁用。 必须先启用模块B，然后才能启用模块A。

* 模块A与模块B冲突。您可以禁用模块A和模块B，也可以禁用任意模块，但您 *无法* 同时启用模块A和模块B。

* 依赖关系在 `require` 字段和Magento Open Source `composer.json` 文件。 冲突在 `conflict` 模块中的字段 `composer.json` 文件。 我们使用此信息来构建依赖关系图： `A->B` 表示模块A取决于模块B。

* A *依赖链* 是从模块到另一个模块的路径。 例如，如果模块A依赖于模块B，而模块B依赖于模块C，则依赖链为 `A->B->C`.

如果尝试启用或禁用依赖于其他模块的模块，则错误消息中会显示依赖关系图。

>[!NOTE]
>
>A模块可能 `composer.json` 声明与模块B冲突，但不会相反。

*仅命令行：* 要强制启用或禁用模块（无论其依赖项如何），请使用可选 `--force` 参数。

>[!NOTE]
>
>使用 `--force` 会禁用您的存储区，并导致访问管理员时出现问题。
