---
title: 設定檔案所有權與許可權
description: 請依照下列步驟，為Adobe Commerce和Magento Open Source的內部部署設定檔案系統許可權。
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---

# 設定檔案所有權與許可權

本主題說明在安裝Adobe Commerce或Magento Open Source之前，如何設定Web伺服器群組的讀寫許可權。 這是必要的，命令列才能將檔案寫入檔案系統。

您使用的程式會有所不同，這取決於您是否使用 [共用託管](#set-permissions-for-one-user-on-shared-hosting) 並擁有一名使用者，或如果您使用 [私人伺服器](#set-ownership-and-permissions-for-two-users) 和有兩個使用者。

## 為一位使用者設定共用託管的許可權

本節探討如何設定預先安裝許可權，如果您以同樣執行網頁伺服器的使用者身分登入應用程式伺服器。 這類設定在共用託管環境中很常見。

若要在安裝應用程式之前設定許可權：

1. 登入您的應用程式伺服器。
1. 使用共用主機提供者提供的檔案管理員應用程式，確認已在下列目錄設定寫入許可權：

   * `vendor` （Composer或壓縮封存安裝）
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * 任何其他靜態資源

1. 如果您有命令列存取權，請依照顯示的順序輸入下列命令：

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   若要選擇在一行中輸入所有命令，請輸入以下內容(假設應用程式安裝在 `/var/www/html/magento2`：

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. 如果您尚未這樣做，請以下列其中一種方式取得應用程式：

   * [Composer中繼套件](../../composer.md)
   * [複製存放庫（僅限貢獻開發人員）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. 在您設定檔案系統擁有權和許可權後， [安裝應用程式](../../advanced.md)

>[!NOTE]
>
>若要在安裝應用程式後進一步限制許可權，您可以 [設定umask](../../next-steps/set-umask.md).

## 設定兩個使用者的擁有權和許可權

本節討論如何設定您自己的伺服器或私人託管設定的擁有權和許可權。 在此型別的設定中，您通常 *無法* 以網頁伺服器使用者身分登入或切換至該使用者。 您通常會以單一使用者身分登入，並以其他使用者身分執行網頁伺服器。

若要設定雙使用者系統的擁有權和許可權：

依照顯示的順序完成下列工作：

* [關於共用群組](#about-the-shared-group)
* [建立檔案系統擁有者，並為使用者提供增強式密碼](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [尋找網頁伺服器使用者的群組](#find-the-web-server-user-group)
* [將檔案系統擁有者放在網頁伺服器群組中](#put-the-file-system-owner-in-the-web-server-group)
* [取得軟體](#get-the-software)
* [設定共用群組的所有權和許可權](#set-ownership-and-permissions-for-the-shared-group)

### 關於共用群組

讓Web伺服器能夠寫入檔案系統中的檔案和目錄，但也要維護 *所有權* 由檔案系統擁有者，兩個使用者必須位於同一個群組中。 這是必要的，這樣兩個使用者就可以共用檔案（包括使用「管理員」或其他網頁型公用程式建立的檔案）的存取權。

本節討論如何建立檔案系統擁有者，並將該使用者放入網頁伺服器的群組中。 您可以視需要使用現有的使用者帳戶；基於安全考量，建議使用者使用強式密碼。

>[!NOTE]
>
>跳至 [尋找網頁伺服器使用者群組](#find-the-web-server-user-group) 如果您打算使用現有的使用者帳戶。

### 建立檔案系統擁有者，並為使用者提供增強式密碼

本節將討論如何建立檔案系統擁有者。 (檔案系統擁有者是 *命令列使用者*.)

若要在CentOS或Ubuntu上建立使用者，請輸入以下命令作為使用者 `root` 許可權：

```bash
adduser <username>
```

若要為使用者提供密碼，請以使用者的身分輸入以下命令 `root` 許可權：

```bash
passwd <username>
```

依照熒幕上的提示為使用者建立密碼。

>[!WARNING]
>
>如果您沒有 `root` 許可權，您可以使用其他本機使用者帳戶。 請確定使用者有強式密碼，然後繼續 [將檔案系統擁有者放在網頁伺服器群組中](#step-3-put-the-file-system-owner-in-the-web-servers-group).

例如，若要建立名為的使用者 `magento_user` 並為使用者輸入密碼，請輸入：

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>由於建立此使用者的目的是提供新增的安全性，因此請務必建立 [增強式密碼](https://en.wikipedia.org/wiki/Password_strength).

### 尋找網頁伺服器使用者群組

若要尋找Web伺服器使用者的群組：

* CentOS：

   ```bash
   grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
   ```

   或

   ```bash
   grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
   ```

通常使用者名稱和群組名稱都是 `apache`.

* Ubuntu： `ps aux | grep apache` 找到Apache使用者，然後 `groups <apache user>` 以尋找群組。

通常使用者名稱和群組名稱都是 `www-data`.

### 將檔案系統擁有者放在網頁伺服器群組中

若要將檔案系統擁有者放在網頁伺服器的主要群組中（假定CentOS和Ubuntu的典型Apache群組名稱），請輸入以下命令作為使用者 `root` 許可權：

* CentOS： `usermod -a -G apache <username>`
* Ubuntu： `usermod -a -G www-data <username>`

>[!NOTE]
>
>此 `-a -G` 選項很重要，因為它們會新增 `apache` 或 `www-data` as a *次要* 群組至使用者帳戶，以保留使用者的 *主要* 群組。 將次要群組新增至使用者帳戶有所幫助 [限制檔案擁有權和許可權](#set-ownership-and-permissions-for-two-users) 以確保共用群組的成員只能存取特定檔案。

例如，若要新增使用者 `magento_user` 至 `apache` CentOS上的主要群組：

```bash
sudo usermod -a -G apache magento_user
```

若要確認您的使用者是Web伺服器群組的成員，請輸入下列命令：

```bash
groups magento_user
```

以下範例結果顯示使用者的主要(`magento`)和次要(`apache`)群組。

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>通常使用者名稱和主要群組名稱相同。

若要完成工作，請重新啟動網頁伺服器：

* Ubuntu： `service apache2 restart`
* CentOS： `service httpd restart`

### 取得軟體

如果您尚未這樣做，請以下列其中一種方式取得軟體：

* [Composer中繼套件](../../composer.md)
* [複製存放庫（僅限貢獻開發人員）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### 設定共用群組的所有權和許可權

若要在安裝應用程式之前設定擁有權和許可權：

1. 以檔案系統擁有者的身分登入應用程式伺服器，或切換到檔案系統擁有者。
1. 依照顯示的順序輸入下列命令：

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

若要選擇在一行中輸入所有命令，請輸入以下內容(假設應用程式安裝在 `/var/www/html/magento2` 而且網頁伺服器群組名稱為 `apache`：

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

如果檔案系統許可權設定不正確，且檔案系統擁有者無法變更，您可以輸入命令作為使用者 `root` 許可權：

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## 切換到檔案系統擁有者

執行本主題中的其他工作後，請輸入下列其中一個命令以切換到該使用者：

* Ubuntu： `su <username>`
* CentOS： `su - <username>`

例如，

```bash
su magento_user
```
