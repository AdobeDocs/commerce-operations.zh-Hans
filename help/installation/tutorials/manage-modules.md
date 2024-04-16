---
title: 启用或禁用模块
description: 按照以下步骤管理Adobe Commerce或Magento Open Source模块。
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---

# 启用或禁用模块

此命令没有先决条件。

## 模块状态

使用以下命令列出已启用和禁用的模块：

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

位置

* `--enabled` 列出了所有已启用的模块。
* `--disabled` 列出了所有禁用的模块。
* `<module-list>` 是以空格分隔的模块列表，用于检查状态。 如果任何模块名称包含特殊字符，请用单引号或双引号将名称括起来。

>[!NOTE]
>
>不能直接在云项目上启用或禁用模块。 您必须在本地运行这些命令，然后将更改推送到 `app/etc/config.php` 环境文件。 请参阅 [专业项目工作流：部署工作流](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow).

## 模块启用、禁用

要启用或禁用可用模块，请使用以下命令：

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

位置

* `<module-list>` 是要启用或禁用的模块的以空格分隔的列表。 如果任何模块名称包含特殊字符，请用单引号或双引号将名称括起来。
* `--all` 以同时启用或禁用所有模块。
* `-f` 或 `--force` 强制启用或禁用模块，而不考虑依赖关系。 在使用此选项之前，请参阅 [关于启用和禁用模块](#about-enabling-and-disabling-modules).
* `-c` 或 `--clear-static-content` 清理 [生成的静态视图文件](../../configuration/cli/static-view-file-deployment.md).

  如果存在多个同名文件并且您未全部清除，则无法清除静态视图文件可能会导致问题。

  换句话说，因为 [静态文件回退](../../configuration/cli/static-view-file-deployment.md) 规则（如果未清除静态文件并且存在多个名为的文件） `logo.svg` 不同，回退可能会导致显示错误的文件。

例如，要禁用 `Magento_Weee` 模块，输入：

```bash
bin/magento module:disable Magento_Weee
```

有关启用和禁用模块的重要信息，请参阅 [关于启用和禁用模块](#about-enabling-and-disabling-modules).

## 更新数据库

如果启用了一个或多个模块，请运行以下命令来更新数据库：

```bash
bin/magento setup:upgrade
```

然后清理缓存：

```bash
bin/magento cache:clean
```

## 关于启用和禁用模块

Adobe Commerce允许您启用或禁用当前可用的模块；换言之，启用或禁用任何Adobe提供的模块或任何当前可用的第三方模块。

某些模块具有对其他模块的依赖关系，在这种情况下，您可能无法启用或禁用模块，因为它具有对其他模块的依赖关系。

此外，可能会 *冲突* 无法同时启用的模块。

示例：

* 模块A依赖于模块B。除非先禁用模块A，否则不能禁用模块B。

* 模块A依赖于模块B，二者均被禁用。 在启用模块A之前，必须启用模块B。

* 模块A与模块B冲突。您可以禁用模块A和模块B，也可以禁用任一模块，但您可以 *无法* 同时启用模块A和模块B。

* 依赖关系在 `require` Adobe Commerce中的字段 `composer.json` 每个模块的文件。 冲突在 `conflict` 模块中的字段 `composer.json` 文件。 我们使用这些信息来构建依赖关系图： `A->B` 表示模块A依赖于模块B。

* A *依赖关系链* 是从模块到另一个模块的路径。 例如，如果模块A依赖于模块B，而模块B依赖于模块C，则依赖链为 `A->B->C`.

如果尝试启用或禁用依赖其他模块的模块，则依赖关系图将显示在错误消息中。

>[!NOTE]
>
>可能是A模块 `composer.json` 声明与模块B冲突，但不声明相反冲突。

*仅命令行：* 要强制启用或禁用模块，而不考虑其依赖关系，请使用可选的 `--force` 参数。

>[!NOTE]
>
>使用 `--force` 可能会禁用您的商店，并导致访问管理员时出现问题。
