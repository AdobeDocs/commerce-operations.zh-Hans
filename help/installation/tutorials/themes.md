---
title: 卸载主题
description: 按照以下步骤卸载Adobe Commerce或Magento Open Source主题。
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# 卸载主题

使用此命令之前，必须知道主题的相对路径。 主题位于的子目录中 `<magento_root>/app/design/<area name>`. 您必须指定以区域开头的主题路径，即 `frontend` （对于店面主题）或 `adminhtml` （对于管理主题）。

例如，Adobe Commerce和Magento Open Source提供的Luma主题的路径为 `frontend/Magento/luma`.

有关主题的更多信息，请参阅 [主题结构](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## 卸载主题概述

本节讨论如何卸载一个或多个主题，可以选择从文件系统卸载主题的代码。 您可以先创建备份，以便以后恢复数据。

此命令卸载 *仅限* 中指定的主题 `composer.json`；换言之，作为编辑器包提供的主题。 如果您的主题不是编辑器包，则必须通过以下方式手动卸载它：

* 更新 `parent` 中的节点信息 `theme.xml` 以移除对主题的引用。
* 正在从文件系统删除主题代码。

  [有关主题继承的更多信息](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## 卸载主题

命令用法：

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

位置

* `{theme path}` 是主题的相对路径，从区域名称开始。 例如，Adobe Commerce和Magento Open Source提供的空白主题的路径为 `frontend/Magento/blank`.
* `--backup-code` 备份代码库，如下面的段落所述。
* `--clear-static-content` 已生成清理 [静态视图文件](../../configuration/cli/static-view-file-deployment.md)，这是正确显示静态视图文件所必需的。

该命令执行以下任务：

1. 验证指定的主题路径是否存在；如果不存在，命令将终止。
1. 验证主题是否为Composer包；如果不是，命令将终止。
1. 检查依赖关系，如果存在任何未满足的依赖关系，则终止该命令。

   要解决此问题，您可以同时卸载所有主题，也可以先根据主题卸载。

1. 验证主题是否未被使用；如果正在使用它，则命令终止。
1. 验证主题是否不是虚拟主题的基础；如果它是虚拟主题的基础，则命令终止。
1. 将商店置于维护模式。
1. 如果 `--backup-code` 指定时，备份代码库，但不包括 `pub/static`， `pub/media`、和 `var` 目录。

   备份文件名为 `var/backups/<timestamp>_filesystem.tgz`

   您可以随时使用恢复备份 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

1. 从删除主题 `theme` 数据库表。
1. 使用以下方式从代码库中移除主题 `composer remove`.
1. 清理缓存。
1. 清理生成的类
1. 如果 `--clear-static-content` 已指定，清除 [生成的静态视图文件](../../configuration/cli/static-view-file-deployment.md).

例如，如果尝试卸载另一个主题所依赖的主题，则会显示以下消息：

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

一种选择是同时卸载这两个主题，如备份代码库一样：

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

显示类似于以下内容的消息：

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
>要卸载管理员主题，还必须从组件的依赖项注入配置中删除该主题， `<component root directory>/etc/di.xml`.
