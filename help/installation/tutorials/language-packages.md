---
title: 解除安裝語言套件
description: 請依照下列步驟解除安裝Adobe Commerce或Magento Open Source語言套件。
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# 解除安裝語言套件

本節討論如何解除安裝一或多個語言套件，選擇性地從檔案系統包含語言套件的程式碼。 您可以先建立備份，以便稍後還原資料。

此命令會解除安裝 *僅限* 中指定的語言套件 `composer.json`；換言之，就是提供為Composer套件的語言套件。 如果您的語言套件不是Composer套件，您必須從檔案系統移除語言套件程式碼，以手動方式解除安裝它。

您可以隨時使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

命令使用方式：

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

語言套件解除安裝命令會執行下列工作：

1. 檢查相依性；如果是，則命令終止。

   若要解決此問題，您可以同時解除安裝所有相依的語言套件，也可以先解除安裝相依的語言套件。

1. 若 `--backup code` 指定，備份檔案系統(不包括 `var` 和 `pub/static` 目錄) `var/backups/<timestamp>_filesystem.tgz`
1. 使用以下專案從程式碼基底移除語言套件檔案： `composer remove`.
1. 清除快取。

例如，如果您嘗試解除安裝其他語言套件所依賴的語言套件，則會顯示下列訊息：

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

另一種選擇是在備份程式碼基底後解除安裝兩種語言套件：

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

類似下列顯示的訊息：

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
