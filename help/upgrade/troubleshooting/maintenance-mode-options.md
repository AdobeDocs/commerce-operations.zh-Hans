---
title: 升級的維護模式選項
description: 建立自訂維護模式頁面，供您的客戶在執行升級時於您的Adobe Commerce或Magento Open Source店面檢視。
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 升級的維護模式選項

本主題說明如何建立自訂維護頁面，以在升級Magento應用程式時顯示給使用者。 建立自訂頁面為選用，但建議使用，因為您的網站在升級期間可供存取。

建立自訂頁面，將使用者重新導向至該頁面，會阻止對該網站的任何存取，並會通知您的使用者該網站正在進行維護。

>[!NOTE]
>
>您必須以使用者身分執行本節中的工作， `root` 許可權。 在開發人員模式中無法設定自訂維護頁面。

## 建立自訂維護頁面

若要建立維護頁面並重新導向至該頁面，請先建立維護頁面，命名為：

- Apache： `<web server docroot>/maintenance.html`
- Nginx： `<magento_root>/maintenance.html`

新增下列內容：

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Apache的自訂維護頁面

本節探討如何建立自訂維護頁面，以及如何將流量重新導向至該頁面。

本節中的範例說明如何修改下列檔案，這是設定維護頁面的一種方式：

- Apache 2.4： `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2： `/etc/apache2/sites-available/default` (Ubuntu)、 `/etc/httpd/conf/httpd.conf` (CentOS)

若要將流量重新導向至自訂維護頁面：

1. 更新您的Apache設定以執行下列操作：

   - 將所有流量重新導向至維護頁面
   - 允許列出某些IP，以便管理員可以升級Magento軟體。

   以下範例允許清單192.0.2.110。

   在Apache設定檔案的結尾新增下列內容：

   ```terminal
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. 重新啟動Apache：

   - CentOS： `service httpd restart`
   - Ubuntu： `service apache2 restart`

1. 輸入下列命令：

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [升級您的系統](../implementation/perform-upgrade.md).
1. 測試您的網站以確保其正常運作。
1. 升級完成後，刪除 `maintenance.enable`.

## Nginx的自訂維護頁面

本節探討如何建立自訂維護頁面，以及如何將流量重新導向至該頁面。

若要將流量重新導向至自訂維護頁面：

1. 使用文字編輯器開啟包含伺服器區塊的nginx組態檔。
1. 將下列專案新增至伺服器區塊(`server` 僅供清楚說明之用；請勿新增第二個伺服器區塊)。

   以下允許清單列出Magento安裝所在系統上的IP位址192.0.2.110和192.0.2.115 `/var/www/html/magento2`：

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 輸入下列命令：

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. 重新載入nginx設定：

   ```bash
   service nginx reload
   ```

1. [升級您的系統](../implementation/perform-upgrade.md).
1. 測試您的網站以確保其正常運作。
1. 升級完成後，請刪除或重新命名 `maintenance.enable`
1. 重新載入nginx設定：

   ```bash
   service nginx reload
   ```
