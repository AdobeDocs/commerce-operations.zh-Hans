---
title: 卸载语言包
description: 按照以下步骤卸载Adobe Commerce或Magento Open Source语言包。
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# 卸载语言包

本节讨论如何从文件系统卸载一个或多个语言包，或者包括语言包的代码。 您可以先创建备份，以便以后恢复数据。

此命令卸载 *仅限* 中指定的语言包 `composer.json`；换言之，即作为编辑器包提供的语言包。 如果您的语言包不是编辑器包，则必须通过从文件系统删除语言包代码来手动卸载它。

您可以随时使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

命令用法：

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

语言包卸载命令执行以下任务：

1. 检查依赖关系；如果是，则命令终止。

   要解决此问题，您可以同时卸载所有从属语言包，也可以先卸载从属语言包。

1. 如果 `--backup code` 指定，备份文件系统(不包括 `var` 和 `pub/static` 目录) `var/backups/<timestamp>_filesystem.tgz`
1. 使用以下方式从代码库中移除语言包文件 `composer remove`.
1. 清理缓存。

例如，如果您尝试卸载其他语言包所依赖的语言包，则会显示以下消息：

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

另一种选择是在备份代码库后卸载两种语言包：

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

与以下内容类似的消息：

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
