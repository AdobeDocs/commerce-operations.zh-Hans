---
title: 檔案系統存取許可權
description: 瞭解如何為開發和生產系統設定Commerce應用程式檔案系統的擁有者或擁有者。
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# 檔案系統存取許可權

本節討論如何為開發和生產系統設定Commerce檔案系統的擁有者或擁有者。 在繼續之前，請檢閱中討論的概念 [檔案系統擁有權和許可權概觀](../../installation/prerequisites/file-system/overview.md).

本主題著重於Commerce開發和生產系統。 如果您正在安裝Commerce，請參閱 [設定安裝前的擁有權和許可權](../../installation/prerequisites/file-system/configure-permissions.md).

以下各節討論一或兩個檔案系統擁有者的需求。 這表示：

- **一位使用者** — 通常在共用託管提供者上需要，可讓您僅存取伺服器上的一名使用者。此使用者可以使用FTP登入、傳輸檔案，而且此使用者也會執行網頁伺服器。

- **兩個使用者** — 如果您執行自己的Commerce伺服器，建議您使用兩個使用者：一個用來傳輸檔案和執行命令列公用程式，另一個則是用於Web伺服器軟體的個別使用者。 如果可能的話，這會比較好，因為它比較安全。

   相反地，您有不同的使用者：

   - 執行管理員和店面的網頁伺服器使用者。

   - A _命令列使用者_，此為本機使用者帳戶，可用來登入伺服器。 此使用者會執行Commerce cron作業和命令列公用程式。

## 共用託管的生產檔案系統所有權（一名使用者）

若要使用單一擁有者設定，您必須以執行網頁伺服器的相同使用者身分登入您的Commerce伺服器。 這是共用託管的典型做法。

因為有一個檔案系統擁有者不太安全，建議您儘可能將Commerce部署在生產環境中於私人伺服器，而非共用託管。

### 為預設或開發人員模式設定一個擁有者

在預設或開發人員模式中，使用者必須可寫入下列目錄：

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- 任何其他靜態資源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

您可以使用命令列或共用託管提供者提供的檔案管理員應用程式來設定這些許可權。

### 為生產模式設定一個擁有者

當您準備好將網站部署到生產環境時，您應該從以下目錄中的檔案移除寫入許可權，以提高安全性：

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- 任何其他靜態資源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

若要更新元件、安裝新元件或升級Commerce軟體，上述所有目錄必須為讀寫目錄。

#### 將程式碼檔案和目錄設為唯讀

若要移除網頁伺服器使用者群組中檔案與目錄的寫入許可權：

1. 登入您的Commerce伺服器。

1. 變更至Commerce安裝目錄。

1. 變更為生產模式。

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 移除下列目錄的寫入許可權。

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. 使命令列工具可執行。

   ```bash
   chmod u+x bin/magento
   ```

#### 將程式碼檔案和目錄設為可寫入

若要讓檔案和目錄可寫入，以便更新元件和升級Commerce軟體：

1. 登入您的Commerce伺服器。
1. 變更至Commerce安裝目錄。
1. 輸入下列命令：

   ```bash
   chmod -R u+w .
   ```

### 選擇性設定 `magento_umask`

另請參閱 [選擇性設定收件者](../../installation/next-steps/set-umask.md) 在 _安裝指南_.

## 私人託管的生產檔案系統所有權（兩個使用者）

如果您使用自己的伺服器（包括託管提供者的私人伺服器設定），則有兩個使用者：

- 此 **網頁伺服器使用者**，會執行管理員和店面。

   Linux系統通常不會為此使用者提供Shell；您無法以Web伺服器使用者的身分登入Commerce伺服器或切換至該使用者。

- 此 **命令列使用者**，您可在此登入或切換至您的Commerce伺服器。

   Commerce會使用此使用者執行CLI命令和cron。

   >[!INFO]
   >
   >命令列使用者也稱為 _檔案系統擁有者_.

由於這些使用者需要存取相同的檔案，因此建議您建立 [共用群組](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) 兩者都屬於哪一個。 下列程式假設您已完成此操作。

請參閱下列其中一節：

- 處於開發人員或預設模式的兩個檔案系統擁有者
- 兩個檔案系統擁有者處於生產模式

### 設定預設或開發人員模式的兩個擁有者

開發人員與預設模式下的使用者都必須可寫入下列目錄中的檔案：

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

設定 [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) 位元在目錄中，因此許可權一律繼承自父目錄。

>[!INFO]
>
>`setgid` 僅適用於目錄， _not_ 至檔案。

此外，網頁伺服器群組應可寫入這些目錄。 由於這些目錄中可能存在內容，因此請遞回新增許可權。

#### 設定許可權和 `setgid`

要設定 `setgid` 開發人員模式的和許可權：

1. 以檔案系統擁有者的身分登入或切換到您的Commerce伺服器。
1. 依照顯示的順序輸入下列命令：

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### 兩個檔案系統擁有者處於生產模式

當您準備好將網站部署到生產環境時，您應該從以下目錄中的檔案移除寫入許可權，以提高安全性：

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- 任何其他靜態資源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### 將程式碼檔案和目錄設為唯讀

若要移除網頁伺服器使用者群組中檔案與目錄的可寫入許可權：

1. 登入您的Commerce伺服器。
1. 變更至Commerce安裝目錄。
1. 以檔案系統擁有者的身分，輸入以下命令以變更至生產模式：

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 以使用者身分輸入以下命令，具有 `root` 許可權：

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### 將程式碼檔案和目錄設為可寫入

若要讓檔案和目錄可寫入，以便更新元件和升級Commerce軟體：

1. 登入您的Commerce伺服器。
1. 變更至Commerce安裝目錄。
1. 輸入下列命令：

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
