---
title: 修改docroot以提高安全性
description: 防止未經授權的瀏覽器式存取Adobe Commerce或Magento Open Source內部部署檔案系統。
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# 修改docroot以提高安全性

在使用Apache Web Server的標準安裝中，Adobe Commerce和Magento Open Source會安裝到預設的網頁根目錄： `/var/www/html/magento2`.

此 `magento2/` 目錄包含下列專案：

- `pub/`
- `setup/`
- `var/`

應用程式服務來源： `/var/www/html/magento2/pub`. 檔案系統的其餘部分很容易受到攻擊，因為可從瀏覽器存取。
將webroot設定為 `pub/` 目錄可防止網站訪客從瀏覽器存取檔案系統的敏感區域。

本主題說明如何變更現有執行個體上的Apache docroot，以從提供檔案 `pub/` 目錄，這樣會更安全。

## 關於nginx的注意事項

如果您使用 [nginx](../prerequisites/web-server/nginx.md) 和 [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 檔案包含在安裝目錄中，而您可能已經從 `pub/` 目錄。

在定義網站的伺服器區塊中使用時， `nginx.conf.sample` 設定會覆寫伺服器的docroot設定，以從 `pub/` 目錄。 例如，請參閱下列組態中的最後一行：

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## 開始之前

若要完成本教學課程，您需要存取上執行的有效安裝 [LAMP](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) 棧疊：

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x)或OpenSearch (1.2)
- Adobe Commerce或Magento Open Source (2.4+)

>[!NOTE]
>
>請參閱 [必要條件](../prerequisites/overview.md) 和 [安裝指南](../overview.md) 以取得詳細資訊。

## 1.編輯伺服器設定

虛擬主機檔案的名稱和位置取決於您所執行的Apache版本。 此範例顯示Apache v2.4上虛擬主機檔案的名稱和位置。

1. 登入您的應用程式伺服器。
1. 編輯您的虛擬主機檔案：

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. 將路徑新增至 `pub/` 目錄到 `DocumentRoot` 指令：

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. 重新啟動Apache：

   ```bash
   systemctl restart apache2
   ```

## 2.更新您的基底URL

如果您在伺服器的主機名稱或IP位址後附加目錄名稱，可在安裝應用程式時建立基礎URL (例如 `http://192.168.33.10/magento2`)，您需要將其移除。

>[!NOTE]
>
>Replace `192.168.33.10` 與您的伺服器主機名稱搭配使用。

1. 登入資料庫：

   ```bash
   mysql -u <user> -p
   ```

1. 指定您在安裝應用程式時所建立的資料庫：

   ```shell
   use <database-name>
   ```

1. 更新基底URL：

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3.更新env.php檔案

將下列節點附加至 `env.php` 檔案。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

請參閱 [env.php參考](../../configuration/reference/config-reference-envphp.md) 以取得詳細資訊。

## 4.切換模式

[應用程式模式](../../configuration/bootstrap/application-modes.md)，其中包括 `production` 和 `developer`，旨在改善安全性並簡化開發工作。 如名稱所建議，您應切換至 `developer` 在延伸或自訂應用程式時模式並切換至 `production` 在即時環境中執行時的模式。

在模式之間切換是驗證伺服器設定是否正常運作的重要步驟。 您可以使用CLI工具在模式之間切換：

1. 前往您的安裝目錄。
1. 切換至 `production` 模式。

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 重新整理瀏覽器，並確認店面是否正確顯示。
1. 切換至 `developer` 模式。

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 重新整理瀏覽器，並確認店面是否正確顯示。

## 5.確認店面

使用網頁瀏覽器前往店面，確認一切都正常運作。

1. 開啟網頁瀏覽器，並在網址列中輸入伺服器的主機名稱或IP位址。 例如， `http://192.168.33.10`.

   下圖顯示店面頁面的範例。 如果它顯示如下，表示您的安裝成功！

   ![驗證安裝成功的店面](../../assets/installation/install-success_store.png)

   請參閱 [疑難排解章節](https://support.magento.com/hc/en-us/articles/360032994352) 頁面顯示404 （找不到）或無法載入影像、CSS和JS等其他資產。

1. 請嘗試從瀏覽器存取應用程式目錄。 在位址列中，將目錄名稱附加至伺服器的主機名稱或IP位址：

   如果您看到404或「存取遭拒」訊息，表示您已成功限制檔案系統的存取。

   ![存取遭拒](../../assets/installation/access-denied.png)
