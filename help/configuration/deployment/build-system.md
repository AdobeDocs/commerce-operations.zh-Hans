---
title: 建置系統設定
description: 瞭解如何將Commerce部署至組建系統。
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 建置系統設定

您可以有一個符合下列要求的建置系統：

- 所有Commerce程式碼都在與開發和生產系統相同的存放庫中進行原始檔控制
- 請確定下列所有專案皆為 _已包含_ 在原始檔控制中：

   - `app/etc/config.php`
   - `generated` 目錄（和子目錄）
   - `pub/media` 目錄
   - `pub/media/wysiwyg` 目錄（和子目錄）
   - `pub/static` 目錄（和子目錄）

- 必須安裝相容的PHP版本
- 必須安裝撰寫器
- 它有檔案系統所有權和許可權設定，如中所述 [開發、建置和生產系統的先決條件](../deployment/technical-details.md).
- 組建系統不需要安裝Commerce，但必須有程式碼可供使用。

>[!WARNING]
>
>如果資料庫連線已包含在，則不需要資料庫連線 `config.php`；請參閱 [匯出設定](../cli/export-configuration.md). 否則，需要資料庫連線。

>[!INFO]
>
>組建電腦可以位於其自身的主機上，或與已安裝的Commerce系統位於相同的主機上。

## 設定組建電腦

以下各節將討論如何設定組建電腦。

### 安裝撰寫器

首先，檢查是否已安裝Composer：

在命令提示字元中，輸入下列任一命令：

- `composer --help`
- `composer list --help`

如果顯示命令說明，表示已經安裝Composer。

如果顯示錯誤，請使用下列步驟安裝Composer。

若要安裝Composer：

1. 在您的Commerce伺服器上變更為或建立空白目錄。

1. 輸入下列命令：

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

如需其他安裝選項，請參閱 [Composer安裝檔案][composer].

### 安裝PHP

將PHP安裝在 [CentOS] 或 [Ubuntu].

### 設定建置系統

若要設定建置系統：

1. 以檔案系統擁有者的身分登入或切換到檔案系統擁有者。
1. 從原始檔控制中擷取Commerce程式碼。

   如果您使用Git，請使用下列命令：

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. 變更至Commerce根目錄並輸入：

   ```bash
   composer install
   ```

1. 等待相依性更新。
1. 設定擁有權：

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   例如，

   ```bash
   chown -R commerce-username:apache .
   ```

1. 如果您使用Git，請開啟 `.gitignore` 在文字編輯器中。
1. 以下各行開頭使用 `#` 要註解它們的字元：

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. 將變更儲存至 `.gitignore` 並退出文字編輯器。
1. 如果您使用Git，請使用下列命令來確認變更：

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   請參閱 [`.gitignore` 參考資料](../reference/config-reference-gitignore.md) 以取得詳細資訊。

1. 建置系統應使用 [預設模式](../bootstrap/application-modes.md#default-mode) 或 [開發人員模式](../bootstrap/application-modes.md#developer-mode)：

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` 為必填欄位。 它可以是 `default` 或 `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
