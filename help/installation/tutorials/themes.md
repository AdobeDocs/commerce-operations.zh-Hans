---
title: 卸载主题
description: 按照以下步骤卸载Adobe Commerce或Magento Open Source主题。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# 卸载主题

在使用此命令之前，您必须知道主题的相对路径。 主题位于的子目录中 `<magento_root>/app/design/<area name>`. 必须指定以区域开头的主题路径，该区域为 `frontend` （对于店面主题）或 `adminhtml` ( [管理员](https://glossary.magento.com/magento-admin) 主题)。

例如，Luma的路径 [主题](https://glossary.magento.com/theme) 提供Adobe Commerce，且Magento Open Source `frontend/Magento/luma`.

有关主题的更多信息，请参阅 [主题结构](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## 卸载主题概述

本节将讨论如何卸载一个或多个主题，其中可选地包括文件系统中的主题代码。 您可以先创建备份，以便稍后恢复数据。

此命令将卸载 *仅* 中指定的主题 `composer.json`;换言之，提供 [编辑器](https://glossary.magento.com/composer) 包。 如果您的主题不是编辑器包，则必须通过以下方式手动卸载它：

* 更新 `parent` 节点信息 `theme.xml` 删除对主题的引用。
* 正在从文件系统中删除主题代码。

   [有关主题继承的更多信息](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## 卸载主题

命令用法：

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

其中

* `{theme path}` 是主题的相对路径，以区域名称开头。 例如，随Adobe Commerce和Magento Open Source一起提供的空白主题的路径为 `frontend/Magento/blank`.
* `--backup-code` 按照以下各段所述备份代码库。
* `--clear-static-content` 清理生成的 [静态视图文件](../../configuration/cli/static-view-file-deployment.md)，这是导致静态视图文件正确显示所必需的。

该命令执行以下任务：

1. 验证指定的主题路径是否存在；如果不支持，则命令将终止。
1. 验证主题是否为编辑器包；如果不支持，则命令将终止。
1. 检查依赖关系，如果存在任何未满足的依赖关系，则终止命令。

   要解决此问题，您可以同时卸载所有主题，也可以先卸载，具体取决于主题。

1. 验证主题是否未被使用；如果正在使用，则命令将终止。
1. 验证主题不是虚拟主题的基础；如果虚拟主题的基础，则命令将终止。
1. 将存储置于维护模式。
1. 如果 `--backup-code` ，请备份代码库，不包括 `pub/static`, `pub/media`和 `var` 目录。

   备份文件名为 `var/backups/<timestamp>_filesystem.tgz`

   您可以随时使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

1. 从 `theme` 数据库表。
1. 使用从代码库中删除主题 `composer remove`.
1. 清除 [缓存](https://glossary.magento.com/cache).
1. 清除生成的类
1. 如果 `--clear-static-content` 已指定，已清理 [生成的静态视图文件](../../configuration/cli/static-view-file-deployment.md).

例如，如果您尝试卸载另一个主题所依赖的主题，则会显示以下消息：

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

一种替代方法是在备份代码库时同时卸载这两个主题：

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

与以下内容类似的消息显示：

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>卸载 [管理员](https://glossary.magento.com/admin) 主题中，您还必须将其从组件的 [依赖注入](https://glossary.magento.com/dependency-injection) 配置， `<component root directory>/etc/di.xml`.
