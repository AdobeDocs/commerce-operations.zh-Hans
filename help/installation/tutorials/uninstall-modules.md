---
title: 卸载模块
description: 按照以下步骤卸载Adobe Commerce或Magento Open Source模块。
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# 卸载模块

本节讨论如何卸载一个或多个模块。 在卸载过程中，可以选择删除模块的代码、数据库架构和数据库数据。 您可以先创建备份，以便以后恢复数据。

只有在确定不会使用某个模块时，才应卸载该模块。 您可以禁用模块，而不是卸载模块，如中所述 [启用或禁用模块](manage-modules.md).

>[!NOTE]
>
>此命令仅检查在中声明的依赖关系 `composer.json` 文件。 如果卸载的模块是 _非_ 在中定义 `composer.json` 文件，此命令会卸载模块而不检查依赖关系。 此命令可以 _非_&#x200B;但是，要从文件系统中删除模块的代码。 必须使用文件系统工具删除模块的代码(例如， `rm -rf <path to module>`)。 作为替代方法，您可以 [disable](manage-modules.md) 非编辑器模块。

命令用法：

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

位置 `{ModuleName}` 指定模块名称 `<VendorName>_<ModuleName>` 格式。 例如，客户模块名称为 `Magento_Customer`. 要获取模块名称列表，请输入 `magento module:status`

模块uninstall命令执行以下任务：

1. 验证指定的模块是否存在于代码库中，以及是否由Composer安装的包。

   此命令有效 _仅限_ 使用定义为编辑器包的模块。

1. 检查与其他模块的依赖关系，如果存在任何未满足的依赖关系，则终止该命令。

   要解决此问题，您可以同时卸载所有模块，也可以先卸载相关模块。

1. 请求确认以继续。
1. 将商店置于维护模式。
1. 处理以下命令选项。

   | Option | 含义 | 备份文件名和位置 |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | 备份文件系统(不包括 `var` 和 `pub/static` 目录)。 | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | 备份pub/media目录 | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | 备份数据库。 | `var/backups/<timestamp>_db.gz` |

1. 如果 `--remove-data` 指定时，删除模块的中定义的数据库架构和数据 `Uninstall` 类。

   对于要卸载的每个指定模块，调用 `uninstall` 方法 `Uninstall` 类。 此类必须继承自 [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. 从删除指定的模块 `setup_module` 数据库表。
1. 从的模块列表中删除指定的模块 [部署配置](../../configuration/reference/deployment-files.md).
1. 使用以下方式从代码库中移除代码 `composer remove`.

   >[!NOTE]
   >
   >卸载模块 _始终_ 运行 `composer remove`. 此 `--remove-data` 选项删除由模块定义的数据库数据和架构 `Uninstall` 类。

1. 清理缓存。
1. 更新生成的类。
1. 如果 `--clear-static-content` 已指定，清除 [生成的静态视图文件](../../configuration/cli/static-view-file-deployment.md).
1. 使存储退出维护模式。

例如，如果尝试卸载另一个模块所依赖的模块，则会显示以下消息：

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

一种选择是在备份模块文件系统后卸载两个模块， `pub/media` 文件和数据库表，但 _非_ 删除模块的数据库架构或数据：

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

显示类似于以下内容的消息：

```terminal
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>如果尝试卸载与另一模块具有依赖关系的模块，则会显示错误。 在这种情况下，无法卸载一个模块；必须同时卸载这两个模块。

## 回滚文件系统、数据库或媒体文件

要将代码库恢复到备份时的状态，请使用以下命令：

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

位置 `<filename>` 是中备份文件的名称 `<app_root>/var/backups` 目录。 要显示备份文件列表，请输入 `magento info:backups:list`

>[!WARNING]
>
>此命令在还原指定文件或数据库之前删除它们。 例如， `--media-file` 选项删除下的媒体资产 `pub/media` 目录，然后再从指定的回退文件还原。 使用此命令之前，请确保您未更改要保留的文件系统或数据库。

>[!NOTE]
>
>要显示可用备份文件列表，请输入 `magento info:backups:list`

此命令执行以下任务：

1. 将商店置于维护模式。
1. 验证备份文件名。
1. 如果指定代码回滚文件：

   a.验证回退目标位置是否可写(请注意 `pub/static` 和 `var` 文件夹将被忽略)。

   b.删除应用程序安装目录下的所有文件和目录。

   c.将存档文件提取到目标位置。

1. 如果指定数据库回滚文件：

   a.删除整个数据库。

   b.使用数据库备份还原数据库。

1. 如果指定介质回滚文件：

   a.验证回退目标位置是否可写。

   b.删除以下项下的所有文件和目录： `pub/media`

   c.将存档文件提取到目标位置。

1. 使存储退出维护模式。

例如，要恢复代码（即文件系统）备份，请按所示顺序输入以下命令：

* 显示备份列表：

   ```bash
   magento info:backups:list
   ```

* 恢复名为的文件备份 `1433876616_filesystem.tgz`：

   ```bash
   magento setup:rollback --code-file="1433876616_filesystem.tgz"
   ```

   显示类似于以下内容的消息：

   ```terminal
   Enabling maintenance mode
   Code rollback is starting ...
   Code rollback filename: 1433876616_filesystem.tgz
   Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
   [SUCCESS]: Code rollback has completed successfully.
   Disabling maintenance mode
   ```

>[!NOTE]
>
>运行 `magento` 命令而不更改目录，您可能需要输入 `cd pwd`.
