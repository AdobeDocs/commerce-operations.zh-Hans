---
title: 使用Nginx設定多個網站
description: 按照本教學課程操作，使用Nginx設定多個網站。
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# 使用Nginx設定多個網站

我們假設：

- 您正在使用開發機器（筆記型電腦、虛擬機器器或類似物件）。

   在託管環境中部署多個網站可能需要執行其他工作；如需詳細資訊，請洽詢您的託管提供者。

   在雲端基礎結構上設定Adobe Commerce需要其他工作。 完成本主題中討論的任務後，請參閱 [設定多個網站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _雲端基礎結構上的Commerce指南_.

- 您可以在一個虛擬主機檔案中接受多個網域，或為每個網站使用一個虛擬主機；虛擬主機設定檔案位於 `/etc/nginx/sites-available`.
- 您使用 `nginx.conf.sample` Commerce提供的，且僅包含本教學課程中討論的修改。
- Commerce軟體安裝在 `/var/www/html/magento2`.
- 您有預設以外的兩個網站：

   - `french.mysite.mg` 使用網站程式碼 `french` 和存放區檢視代碼 `fr`
   - `german.mysite.mg` 使用網站程式碼 `german` 和存放區檢視代碼 `de`
   - `mysite.mg` 是預設網站和預設商店檢視

>[!TIP]
>
>請參閱 [建立網站](ms-admin.md#step-2-create-websites) 和 [建立商店檢視](ms-admin.md#step-4-create-store-views) 以取得尋找這些值的協助。

以下是使用nginx設定多個網站的藍圖：

1. [設定網站、商店和商店檢視](ms-admin.md) 在Admin中。
1. 建立 [Nginx虛擬主機](#step-2-create-nginx-virtual-hosts))以對應多個網站或每個Commerce網站一個Nginx虛擬主機（詳細步驟如下）。
1. 傳遞下列專案的值： [影像變數](ms-overview.md) `$MAGE_RUN_TYPE` 和 `$MAGE_RUN_CODE` 使用Magento提供的nginx `nginx.conf.sample` （步驟詳見下文）。

   - `$MAGE_RUN_TYPE` 可以是 `store` 或 `website`：

      - 使用 `website` 將您的網站載入您的店面。
      - 使用 `store` 以載入店面中的任何商店檢視。
   - `$MAGE_RUN_CODE` 是不重複網站或商店檢視代碼，對應至 `$MAGE_RUN_TYPE`.


1. 更新Commerce管理員的基本URL設定。

## 步驟1：在「管理員」中建立網站、商店和商店檢視

另請參閱 [在「管理員」中設定多個網站、商店和商店檢視](ms-admin.md).

## 步驟2：建立nginx虛擬主機

此步驟會討論如何在店面載入網站。 您可以使用網站或商店檢視；如果您使用商店檢視，則必須相應地調整引數值。 您必須以使用者身分完成本節中的工作， `sudo` 許可權。

只要使用一個 [nginx虛擬主機檔案](#step-2-create-nginx-virtual-hosts)，您可保持簡潔nginx設定。 透過使用數個虛擬主機檔案，您可以自訂每個存放區(以使用自訂位置 `french.mysite.mg` 例如)。

**若要建立一個虛擬主機** （簡化）：

此設定會擴展 [nginx設定](../../installation/prerequisites/web-server/nginx.md).

1. 開啟文字編輯器，並將以下內容新增至名為的新檔案 `/etc/nginx/sites-available/magento`：

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 將變更儲存至檔案並退出文字編輯器。
1. 驗證伺服器組態：

   ```bash
   nginx -t
   ```

1. 如果成功，會顯示下列訊息：

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果顯示錯誤，請檢查虛擬主機組態檔的語法。

1. 在中建立符號連結 `/etc/nginx/sites-enabled` 目錄：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

如需有關map指示詞的詳細資訊，請參閱 [有關map指示詞的nginx檔案](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**若要建立多個虛擬主機**：

1. 開啟文字編輯器，並將以下內容新增至名為的新檔案 `/etc/nginx/sites-available/french.mysite.mg`：

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 建立另一個名為的檔案 `german.mysite.mg` 在相同目錄中，包含以下內容：

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 將變更儲存至檔案並退出文字編輯器。
1. 驗證伺服器組態：

   ```bash
   nginx -t
   ```

1. 如果成功，會顯示下列訊息：

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果顯示錯誤，請檢查虛擬主機組態檔的語法。

1. 在中建立符號連結 `/etc/nginx/sites-enabled` 目錄：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## 步驟3：修改nginx.conf.sample

>[!TIP]
>
>不要編輯 `nginx.conf.sample` 檔案；它是核心Commerce檔案，可隨每個新發行版本更新。 請改為複製 `nginx.conf.sample` 重新命名檔案，然後編輯複製的檔案。

**編輯主要應用程式的PHP入口點**：

若要修改 `nginx.conf.sample` 檔案**：

1. 開啟文字編輯器並檢閱 `nginx.conf.sample` 檔案，`<magento2_installation_directory>/nginx.conf.sample`. 尋找下列章節：

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. 更新 `nginx.conf.sample` 檔案，在include陳述式前具有下列兩行：

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

更新主要應用程式的PHP進入點的範例如下所示：

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## 步驟4：更新基本URL設定

您必須更新以下專案的基底URL： `french` 和 `german` Commerce管理員中的網站。

### 更新法文網站基底URL

1. 登入Commerce管理員並導覽至 **商店** > **設定** > **設定** > **一般** > **Web**.
1. 變更 _設定範圍_ 至 `french` 網站。
1. 展開 **基本URL** 區段並更新 **基本URL** 和 **基本連結URL** 值至 `http://french.magento24.com/`.
1. 展開 **基本URL （安全）** 區段並更新 **安全基底URL** 和 **安全基本連結URL** 值至 `https://french.magento24.com/`.
1. 按一下 **儲存設定** 並儲存設定變更。

### 更新德文網站基底URL

1. 登入Commerce管理員並導覽至 **商店** > **設定** > **設定** > **一般** > **Web**.
1. 變更 _設定範圍_ 至 `german` 網站。
1. 展開 **基本URL** 區段並更新 **基本URL** 和 **基本連結URL** 值至 `http://german.magento24.com/`.
1. 展開 **基本URL （安全）** 區段並更新 **安全基底URL** 和 **安全基本連結URL** 值至 `https://german.magento24.com/`.
1. 按一下 **儲存設定** 並儲存設定變更。

### 清除快取

執行以下命令以清除 `config` 和 `full_page` 快取。

```bash
bin/magento cache:clean config full_page
```

## 驗證您的網站

除非您為商店的URL設定了DNS，否則您必須將靜態路由新增到中的主機。 `hosts` 檔案：

1. 找到您的作業系統 `hosts` 檔案。
1. 以下列格式新增靜態路由：

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. 前往瀏覽器中的下列URL之一：

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 在託管環境中部署多個網站可能需要執行其他工作；如需詳細資訊，請洽詢您的託管提供者。
>- 在雲端基礎結構上設定Adobe Commerce需要其他工作；請參閱 [設定多個Cloud網站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _雲端基礎結構上的Commerce指南_.


### 疑難排除

- 如果您的法文和德文網站傳回404s，但您的管理員載入，請確定您已完成 [步驟6：將商店程式碼新增至基底URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- 如果所有URL都傳回404s，請確定您已重新啟動網頁伺服器。
- 如果管理員無法正常運作，請確定您正確設定虛擬主機。
