---
title: 為您的搜尋引擎設定Nginx
description: 請依照下列步驟，使用Nginx網頁伺服器設定搜尋引擎，以供Adobe Commerce和Magento Open Source的內部部署使用。
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# 為您的搜尋引擎設定Nginx

{{$include /help/_includes/web-server-communication.md}}

## 設定Proxy

>[!NOTE]
>
>2.4.4版新增OpenSearch支援。OpenSearch是相容的Elasticsearch復本。 另請參閱 [將Elasticsearch移轉至OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 以取得詳細資訊。

本節探討如何將nginx設定為 *不安全* Proxy，讓Adobe Commerce能夠使用在此伺服器上執行的搜尋引擎。 本節不討論設定HTTP基本驗證；這將在中討論 [與nginx的安全通訊](#secure-communication-with-nginx).

>[!NOTE]
>
>在此範例中，Proxy不受保護的原因是它更容易設定和驗證。 您可以視需要搭配此Proxy使用TLS；若要這麼做，請務必將Proxy資訊新增至安全伺服器區塊設定。

### 指定全域組態中的其他組態檔

確定您的全域 `/etc/nginx/nginx.conf` 包含下列行，以便載入以下各節中討論的其他組態檔案：

```conf
include /etc/nginx/conf.d/*.conf;
```

### 將nginx設定為Proxy

本節說明如何指定可以存取nginx伺服器的使用者。

1. 使用文字編輯器建立檔案 `/etc/nginx/conf.d/magento_es_auth.conf` 包含下列內容：

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. 重新啟動nginx：

   ```bash
   service nginx restart
   ```

1. 輸入下列命令來驗證Proxy是否運作：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，若您的Proxy使用連線埠8080：

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   類似下列的訊息會顯示以指示成功：

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## 與nginx的安全通訊

本節探討如何設定 [HTTP基本驗證](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) 使用您的安全Proxy。 同時使用TLS和HTTP基本驗證可防止任何人攔截與Elasticsearch、OpenSearch或您的應用程式伺服器的通訊。

由於nginx原本就支援HTTP基本驗證，因此建議您改用，例如 [摘要式驗證](https://www.nginx.com/resources/wiki/modules/auth_digest/)，在生產環境中不建議使用。

其他資源：

* [如何在Ubuntu 14.04 (Digital Ocean)上使用Nginx設定密碼驗證](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [使用Nginx進行基本HTTP驗證(HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Elasticsearch的Nginx設定範例](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

如需詳細資訊，請參閱下列章節：

* [建立密碼](#create-a-password)
* [設定nginx的存取權](#set-up-access-to-nginx)
* [設定搜尋引擎的受限制內容](#set-up-a-restricted-context-for-the-search-engine)
* [驗證通訊是否安全](#secure-communication-with-nginx)

### 建立密碼

建議您使用Apache `htpasswd` 為可存取Elasticsearch或OpenSearch的使用者編碼密碼的命令（已命名） `magento_elasticsearch` 在此範例中)。

若要建立密碼：

1. 輸入下列命令以判斷是否 `htpasswd` 已安裝：

   ```bash
   which htpasswd
   ```

   如果路徑顯示，則會安裝該路徑；如果命令未傳回任何輸出， `htpasswd` 未安裝。

1. 如有必要，請安裝 `htpasswd`：

   * Ubuntu： `apt-get -y install apache2-utils`
   * CentOS： `yum -y install httpd-tools`

1. 建立 `/etc/nginx/passwd` 儲存密碼的目錄：

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >基於安全考量， `<filename>` 應隱藏；也就是說，它必須以句點開頭。

1. *（選擇性）。* 若要將其他使用者新增至您的密碼檔案，請輸入相同的命令，但不使用 `-c` （建立）選項：

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. 驗證以下專案的內容： `/etc/nginx/passwd` 是正確的。

### 設定nginx的存取權

本節說明如何指定可以存取nginx伺服器的使用者。

>[!WARNING]
>
>顯示的範例是 *不安全* proxy。 若要使用安全Proxy，請將下列內容（監聽連線埠除外）新增至您的安全伺服器區塊。

使用文字編輯器來修改 `/etc/nginx/conf.d/magento_es_auth.conf` （不安全）或您的安全伺服器區塊，其內容如下：

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>上述範例中顯示的搜尋引擎監聽連線埠只是範例。 基於安全考量，建議您使用非預設監聽連線埠。

### 設定搜尋引擎的受限制內容

本節探討如何指定誰可以存取搜尋引擎伺服器。

1. 輸入以下命令以建立儲存驗證組態的目錄：

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. 使用文字編輯器建立檔案 `/etc/nginx/auth/magento_elasticsearch.conf` 包含下列內容：

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. 如果您設定安全Proxy，請刪除 `/etc/nginx/conf.d/magento_es_auth.conf`.
1. 重新啟動nginx並繼續下一節：

   ```bash
   service nginx restart
   ```

#### 驗證

{{$include /help/_includes/verify-secure-communication.md}}
