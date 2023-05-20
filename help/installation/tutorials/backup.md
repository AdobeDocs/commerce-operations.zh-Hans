---
title: 備份及復原檔案系統、媒體及資料庫
description: 請依照下列步驟備份和還原Adobe Commerce或Magento Open Source應用程式。
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# 備份及復原檔案系統、媒體及資料庫

此命令可讓您備份：

* 檔案系統(不包括 `var` 和 `pub/static` 目錄)
* 此 `pub/media` 目錄
* 資料庫

備份會儲存在 `var/backups` 目錄，並可隨時使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

備份之後，您可以 [復原](#rollback) 稍後。

>[!TIP]
>
>如需雲端基礎結構專案的Adobe Commerce，請參閱 [快照與備份管理](https://devdocs.magento.com/cloud/project/project-webint-snap.html) 在 _雲端指南_.

## 啟用備份

備份功能預設為停用。 若要啟用，請輸入下列CLI命令：

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**淘汰通知：**
>備份功能自2.1.16、2.2.7和2.3.0起已過時。我們建議調查其他備份技術和二進位備份工具（例如Percona XtraBackup）。

## 設定開啟檔案限制

復原到先前的備份可能會無訊息地失敗，導致使用寫入檔案系統或資料庫的不完整資料 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

有時，長查詢字串會導致使用者配置的記憶體空間因太多遞回呼叫而用盡記憶體。

## 如何設定開啟的檔案 `ulimit`

建議您設定開啟的檔案 [`ulimit`](https://ss64.com/bash/ulimit.html) 將檔案系統使用者設為 `65536` 或更多。

您可以在命令列上執行此操作，也可以透過編輯使用者的shell指令碼將其設為使用者的永久設定。

在繼續之前，如果您尚未這樣做，請切換至 [檔案系統擁有者](../prerequisites/file-system/overview.md).

命令：

```bash
ulimit -s 65536
```

您可以視需要將此變更為較大的值。

>[!NOTE]
>
>開啟檔案的語法 `ulimit` 取決於您使用的UNIX shell。 前面的設定應該適用於CentOS和Ubuntu以及Bash shell。 不過，對於macOS，正確的設定是 `ulimit -S 65532`. 如需詳細資訊，請參閱線上手冊或作業系統參考資訊。

若要選擇性設定使用者的Bash shell中的值：

1. 如果您尚未這樣做，請切換至 [檔案系統擁有者](../prerequisites/file-system/overview.md).
1. 開啟 `/home/<username>/.bashrc` 在文字編輯器中。
1. 新增下列行：

   ```bash
   ulimit -s 65536
   ```

1. 將變更儲存至 `.bashrc` 並退出文字編輯器。

>[!WARNING]
>
>建議您避免為「 」設定值 [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) 在 `php.ini` 因為會導致不完整的倒回，且沒有失敗通知。

## 備份

命令使用方式：

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

指令會執行下列工作：

1. 將存放區置於維護模式。
1. 執行下列其中一個命令選項。

   | 選項 | 含義 | 備份檔案名稱和位置 |
   |--- |--- |--- |
   | `--code` | 備份檔案系統（不包括var和pub/static目錄）。 | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | 備份發佈/媒體目錄。 | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | 備份資料庫。 | `var/backups/<timestamp>/_db.sql` |

1. 將存放區帶出維護模式。

例如，若要備份檔案系統和資料庫，

```bash
bin/magento setup:backup --code --db
```

類似下列顯示的訊息：

```terminal
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## 復原

本節討論如何回覆至您先前建立的備份。 您必須知道要還原之備份檔案的檔案名稱。

若要尋找備份的名稱，請輸入：

```bash
bin/magento info:backups:list
```

備份檔案名稱中的第一個字串是時間戳記。

若要復原至先前的備份，請輸入：

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

例如，若要還原名為的媒體備份 `1440611839_filesystem_media.tgz`，輸入

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

類似下列顯示的訊息：

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
