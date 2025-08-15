---
title: 启用或禁用模块
description: 按照以下步骤管理Adobe Commerce模块。
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
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

* `--enabled`列出了所有已启用的模块。
* `--disabled`列出了所有禁用的模块。
* `<module-list>`是以空格分隔的模块列表，用于检查状态。 如果任何模块名称包含特殊字符，请用单引号或双引号将名称括起来。

>[!NOTE]
>
>不能直接在云项目上启用或禁用模块。 您必须在本地运行这些命令，然后将更改推送到环境的`app/etc/config.php`文件。 请参阅[专业项目工作流：部署工作流](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow)。

## 模块启用、禁用

要启用或禁用可用模块，请使用以下命令：

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

位置

* `<module-list>`是以空格分隔的要启用或禁用的模块列表。 如果任何模块名称包含特殊字符，请用单引号或双引号将名称括起来。
* `--all`以同时启用或禁用所有模块。
* `-f`或`--force`强制启用或禁用模块，而不考虑依赖关系。 使用此选项之前，请参阅[关于启用和禁用模块](#about-enabling-and-disabling-modules)。
* `-c`或`--clear-static-content`清理[生成的静态视图文件](../../configuration/cli/static-view-file-deployment.md)。

  如果存在多个同名文件并且您未全部清除，则无法清除静态视图文件可能会导致问题。

  换言之，由于[静态文件回退](../../configuration/cli/static-view-file-deployment.md)规则，如果不清除静态文件并且有多个名为`logo.svg`的文件不同，则回退可能会导致显示错误的文件。

例如，要禁用`Magento_Weee`模块，请输入：

```bash
bin/magento module:disable Magento_Weee
```

有关启用和禁用模块的重要信息，请参阅[关于启用和禁用模块](#about-enabling-and-disabling-modules)。

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

此外，可能有&#x200B;*个冲突的*&#x200B;模块无法同时启用。

示例：

* 模块A依赖于模块B。除非先禁用模块A，否则不能禁用模块B。

* 模块A依赖于模块B，二者均被禁用。 在启用模块A之前，必须启用模块B。

* 模块A与模块B冲突。您可以禁用模块A和模块B，也可以禁用任一模块，但您&#x200B;*无法*&#x200B;同时启用模块A和模块B。

* 依赖项在每个模块的Adobe Commerce `require`文件的`composer.json`字段中声明。 在模块的`conflict`文件的`composer.json`字段中声明冲突。 我们使用该信息来构建依赖关系图： `A->B`表示模块A依赖模块B。

* *依赖关系链*&#x200B;是从模块到另一个模块的路径。 例如，如果模块A依赖于模块B，而模块B依赖于模块C，则依赖关系链为`A->B->C`。

如果尝试启用或禁用依赖其他模块的模块，则依赖关系图将显示在错误消息中。

>[!NOTE]
>
>模块A的`composer.json`可能与模块B声明冲突，但反之则不然。

*仅限命令行：*&#x200B;若要强制启用或禁用模块，而不考虑其依赖关系，请使用可选的`--force`参数。

>[!NOTE]
>
>使用`--force`可以禁用您的存储区，并导致访问管理员时出现问题。
