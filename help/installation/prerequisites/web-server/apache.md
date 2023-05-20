---
title: Apache
description: 請依照下列步驟安裝和設定Apache Web Server，以供Adobe Commerce和Magento Open Source的內部部署使用。
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---

# Apache

Adobe Commerce支援Apache 2.4.x。

## Apache必要指示

1. 設定 `AllowEncodedSlashes` 在伺服器設定（全域）或虛擬主機設定中，以避免解碼可能導致URL問題的編碼斜線。 例如，透過API在SKU中擷取斜線產品時，您不想要轉換該斜線。 範例區塊不完整，需要其他指令。

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache重寫和htaccess

本主題說明如何啟用Apache 2.4重新寫入，並指定 [分散式組態檔， `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe Commerce和Magento Open Source使用伺服器重寫和 `.htaccess` 以提供Apache的目錄層級指示。 以下指示也包含在本主題的所有其他章節中。

使用此區段來啟用Apache 2.4重新寫入，並指定 [分散式組態檔， `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce和Magento Open Source使用伺服器重寫和 `.htaccess` 以提供Apache的目錄層級指示。

>[!NOTE]
>
>無法啟用這些設定通常會導致您的店面或管理員上沒有顯示任何樣式。

1. 啟用Apache重寫模組：

   ```bash
   a2enmod rewrite
   ```

1. 啟用應用程式以使用分散式 `.htaccess` 設定檔案，請參閱 [Apache 2.4檔案](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >在Apache 2.4中，伺服器的預設網站設定檔案為 `/etc/apache2/sites-available/000-default.conf`.

   例如，您可以新增下列內容至 `000-default.conf`：

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >有時可能需要其他引數。 如需詳細資訊，請參閱 [Apache 2.4檔案](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. 如果您已變更Apache設定，請重新啟動Apache：

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- 如果您從舊版Apache升級，請先尋找 `<Directory "/var/www/html">` 或 `<Directory "/var/www">` 在 `000-default.conf`.
   >- 您必須變更以下專案的值： `AllowOverride` 在您要安裝Adobe Commerce或Magento Open Source軟體之目錄的指示詞中。 例如，若要安裝在Web伺服器docroot中，請編輯 `<Directory /var/www>`.


>[!NOTE]
>
>若未啟用這些設定，通常會導致樣式無法顯示在店面或管理員中。

## Apache必要模組

Adobe Commerce和Magento Open Source需要安裝以下Apache模組：

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## 驗證Apache版本

若要驗證您目前執行的Apache版本，請輸入：

```bash
apache2 -v
```

結果顯示類似以下內容：

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- 如果Apache是 *not* 已安裝，請參閱：
   - [在Ubuntu上安裝或升級Apache](#installing-apache-on-ubuntu)
   - [在CentOS上安裝Apache](#installing-apache-on-centos)

## 在Ubuntu上安裝或升級Apache

以下小節討論如何安裝或升級Apache：

- 安裝Apache
- 升級至Ubuntu上的Apache 2.4以使用PHP 7.4。

### 在Ubuntu上安裝Apache

若要安裝預設版本的Apache：

1. 安裝Apache

   ```bash
   apt-get -y install apache2
   ```

1. 驗證安裝。

   ```bash
   apache2 -v
   ```

   結果顯示類似以下內容：

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. 啟用 [重寫和 `.htaccess`](#apache-rewrites-and-htaccess).

### 在Ubuntu上升級Apache

若要升級至Apache 2.4：

1. 新增 `ppa:ondrej` 存放庫，其中具有Apache 2.4：

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. 安裝Apache 2.4：

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >如果&#39;apt-get install&#39;命令因未滿足的相依性而失敗，請查閱資源，例如 [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. 驗證安裝。

   ```bash
   apache2 -v
   ```

   類似下列的訊息應會顯示：

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. 啟用 [重寫和 `.htaccess`](#apache-rewrites-and-htaccess).

## 在CentOS上安裝Apache

Adobe Commerce和Magento Open Source需要Apache使用伺服器重寫。 您也必須指定可以在下列專案中使用的指令型別： `.htaccess`，應用程式會使用它來指定重寫規則。

安裝和設定Apache基本上是三個步驟的過程：安裝軟體、啟用重寫並指定 `.htaccess` 指令。

### 安裝Apache

1. 安裝Apache 2.4 （如果尚未安裝）。

   ```bash
   yum -y install httpd
   ```

1. 驗證安裝：

   ```bash
   httpd -v
   ```

   類似下列的訊息會顯示以確認安裝成功：

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. 繼續下一節。

   >[!NOTE]
   >
   >即使Apache 2.4預設隨CentOS提供，請參閱下一節以設定它。

### 啟用CentOS的重寫和.htaccess

1. 開啟 `/etc/httpd/conf/httpd.conf` 要編輯的檔案：

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. 找出開頭為的區塊：

   ```conf
   <Directory "/var/www/html">
   ```

1. 變更值 `AllowOverride` 至 `All`.

   例如，

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >以下專案的先前值： `Order` 可能無法在所有情況下運作。 如需詳細資訊，請參閱Apache檔案([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order))。

1. 儲存檔案並退出文字編輯器。

1. 若要套用Apache設定，請重新啟動Apache。

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>無法啟用這些設定通常會導致您的店面或管理員上沒有顯示任何樣式。

### 啟用Ubuntu的重寫和.htaccess

1. 開啟 `/etc/apache2/sites-available/default` 要編輯的檔案：

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. 找出開頭為的區塊：

   `<Directory "/var/www/html">`

1. 變更值 `AllowOverride` 至 `All`.

   例如：

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. 儲存檔案並退出文字編輯器。

1. 設定Apache以使用 `mod_rewrite` 模組：

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. 重新啟動Apache套用變更：

   ```bash
   service apache2 restart
   ```

## 解決403 （禁止）錯誤

如果您在嘗試存取網站時遇到403禁止錯誤，您可以更新Apache設定或虛擬主機設定，以啟用網站的訪客：

### 解決Apache 2.4的403禁止錯誤

若要讓網站訪客能夠存取您的網站，請使用 [Require指示](https://httpd.apache.org/docs/2.4/howto/access.html).

例如：

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>以下專案的先前值： `Order` 可能無法在所有情況下運作。 如需詳細資訊，請參閱 [Apache檔案](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
