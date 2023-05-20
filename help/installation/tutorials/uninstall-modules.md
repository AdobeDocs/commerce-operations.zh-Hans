---
title: 解除安裝模組
description: 請依照下列步驟解除安裝Adobe Commerce或Magento Open Source模組。
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# 解除安裝模組

本節說明如何解除安裝一或多個模組。 解除安裝期間，您可以選擇移除模組的程式碼、資料庫架構和資料庫資料。 您可以先建立備份，以便稍後復原資料。

您必須確定不會使用模組，才能解除安裝模組。 您可以停用模組，而不是解除安裝模組，如中所述 [啟用或停用模組](manage-modules.md).

>[!NOTE]
>
>這個命令只會檢查以下專案中宣告的相依性： `composer.json` 檔案。 如果您解除安裝模組， _not_ 在中定義 `composer.json` 檔案時，這個命令會解除安裝模組，而不檢查相依性。 這個命令可以 _not_&#x200B;不過，請從檔案系統移除模組的程式碼。 您必須使用檔案系統工具來移除模組的程式碼(例如， `rm -rf <path to module>`)。 或者，您可以 [disable](manage-modules.md) 非撰寫器模組。

命令使用方式：

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

位置 `{ModuleName}` 指定模組名稱 `<VendorName>_<ModuleName>` 格式。 例如，客戶模組名稱為 `Magento_Customer`. 若要取得模組名稱清單，請輸入 `magento module:status`

模組解除安裝命令會執行下列工作：

1. 驗證指定的模組是否存在於程式碼庫中，且是否為Composer安裝的套件。

   這個命令可以運作 _僅限_ 使用定義為撰寫器套件的模組。

1. 檢查與其他模組的相依性，如果有任何未滿足的相依性，則終止指令。

   若要解決此問題，您可以同時解除安裝所有模組，也可以先解除安裝相依模組。

1. 要求確認以繼續。
1. 將存放區置於維護模式。
1. 處理下列命令選項。

   | 選項 | 含義 | 備份檔案名稱和位置 |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | 備份檔案系統(排除 `var` 和 `pub/static` 目錄)。 | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | 備份pub/media目錄 | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | 備份資料庫。 | `var/backups/<timestamp>_db.gz` |

1. 若 `--remove-data` 已指定，請移除模組的 `Uninstall` 類別。

   對於要解除安裝的每個指定模組，會叫用 `uninstall` 方法在其中 `Uninstall` 類別。 此類別必須繼承自 [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. 從移除指定的模組 `setup_module` 資料庫表格。
1. 從的模組清單中移除指定的模組 [部署設定](../../configuration/reference/deployment-files.md).
1. 使用以下專案從程式碼基底中移除程式碼： `composer remove`.

   >[!NOTE]
   >
   >解除安裝模組 _一律_ 執行 `composer remove`. 此 `--remove-data` 選項會移除由模組的 `Uninstall` 類別。

1. 清除快取。
1. 更新產生的類別。
1. 若 `--clear-static-content` 已指定，清除 [產生的靜態檢視檔案](../../configuration/cli/static-view-file-deployment.md).
1. 將存放區帶出維護模式。

例如，如果您嘗試解除安裝另一個模組所依賴的模組，則會顯示下列訊息：

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

另一種選擇是在備份模組檔案系統後解除安裝兩個模組。 `pub/media` 檔案和資料庫表格，但 _not_ 移除模組的資料庫結構描述或資料：

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

類似下列顯示的訊息：

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
>如果您嘗試解除安裝與其他模組相依的模組，則會顯示錯誤。 在這種情況下，您無法解除安裝一個模組；您必須解除安裝兩個模組。

## 復原檔案系統、資料庫或媒體檔案

若要將程式碼基底還原成您備份的狀態，請使用下列命令：

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

位置 `<filename>` 是中備份檔案的名稱 `<app_root>/var/backups` 目錄。 若要顯示備份檔案清單，請輸入 `magento info:backups:list`

>[!WARNING]
>
>此命令會先刪除指定的檔案或資料庫，然後再還原它們。 例如， `--media-file` 選項會刪除下的媒體資產 `pub/media` 目錄，然後再從指定的復原檔案還原。 使用此命令之前，請確定您尚未變更要保留的檔案系統或資料庫。

>[!NOTE]
>
>若要顯示可用備份檔案的清單，請輸入 `magento info:backups:list`

此命令會執行下列工作：

1. 將存放區置於維護模式。
1. 驗證備份檔案名稱。
1. 如果您指定程式碼復原檔案：

   a.驗證回覆目的地位置是否可寫入(請注意 `pub/static` 和 `var` 資料夾會被忽略)。

   b.刪除應用程式安裝目錄下的所有檔案和目錄。

   c.將封存檔案擷取至目的地位置。

1. 如果您指定資料庫倒回檔案：

   a.卸除整個資料庫。

   b.使用資料庫備份還原資料庫。

1. 如果您指定媒體倒回檔案：

   a.驗證回覆目的地位置是否可寫入。

   b.刪除以下所有檔案和目錄： `pub/media`

   c.將封存檔案擷取至目的地位置。

1. 將存放區帶出維護模式。

例如，若要還原程式碼（亦即檔案系統）備份，請按下列順序輸入下列命令：

* 顯示備份清單：

   ```bash
   magento info:backups:list
   ```

* 還原名為的檔案備份 `1433876616_filesystem.tgz`：

   ```bash
   magento setup:rollback --code-file="1433876616_filesystem.tgz"
   ```

   類似下列顯示的訊息：

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
>若要執行 `magento` 重新執行命令而不變更目錄，您可能需要輸入 `cd pwd`.
