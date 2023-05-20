---
title: 為您的搜尋引擎設定Apache
description: 請依照下列步驟，使用Apache Web Server設定搜尋引擎，以供Adobe Commerce和Magento Open Source的內部部署使用。
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# 為您的搜尋引擎設定Apache

{{$include /help/_includes/web-server-communication.md}}

## 設定Proxy

>[!NOTE]
>
>2.4.4版新增OpenSearch支援。OpenSearch是相容的Elasticsearch復本。 另請參閱 [將Elasticsearch移轉至OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 以取得詳細資訊。

本節探討如何將Apache設定為 *不安全* Proxy，讓Adobe Commerce能夠使用在此伺服器上執行的搜尋引擎。 本節不討論設定HTTP基本驗證；這將在中討論 [與Apache的安全通訊](#secure-communication-with-apache).

>[!NOTE]
>
>在此範例中，Proxy不受保護的原因是它更容易設定和驗證。 您可以透過此Proxy使用TLS。 如果您想要這麼做，請務必將Proxy資訊新增至您的安全虛擬主機設定。

### 設定Apache 2.4的Proxy

本節探討如何使用虛擬主機設定Proxy。

1. 啟用 `mod_proxy` 如下所示：

   ```bash
   a2enmod proxy_http
   ```

1. 使用文字編輯器開啟 `/etc/apache2/sites-available/000-default.conf`
1. 在檔案頂端新增下列指令：

   ```conf
   Listen 8080
   ```

1. 在檔案底部新增下列內容：

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. 重新啟動Apache：

   ```bash
   service apache2 restart
   ```

1. 輸入下列命令來驗證Proxy是否運作：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，如果您使用Elasticsearch，而Proxy使用連線埠8080：

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

## 與Apache的安全通訊

本節探討如何使用，保護Apache與搜尋引擎之間的通訊 [HTTP基本](https://datatracker.ietf.org/doc/html/rfc2617) 使用Apache進行驗證。 如需更多選項，請參閱下列資源之一：

* [Apache 2.4驗證和授權教學課程](https://httpd.apache.org/docs/2.4/howto/auth.html)

請參閱下列其中一節：

* [建立密碼檔案](#create-a-password)
* [設定安全的虛擬主機](#secure-communication-with-apache)

### 建立密碼

基於安全理由，您可以在網頁伺服器docroot以外的任何地方找到密碼檔案。 在此範例中，我們說明如何將密碼檔案儲存在新目錄中。

#### 安裝htpasswd （如有必要）

首先，檢視您是否擁有Apache `htpasswd` 公用程式的安裝方式如下：

1. 輸入下列命令以判斷是否 `htpasswd` 已安裝：

   ```bash
   which htpasswd
   ```

   如果路徑顯示，則會安裝該路徑；如果命令未傳回任何輸出， `htpasswd` 未安裝。

1. 如有必要，請安裝 `htpasswd`：

   * Ubuntu： `apt-get -y install apache2-utils`
   * CentOS： `yum -y install httpd-tools`

#### 建立密碼檔案

以使用者身分輸入以下命令，並附上 `root` 許可權：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

位置

* `<username>` 可以是：

   * 設定cron：網頁伺服器使用者或其他使用者。

   在此範例中，我們使用Web伺服器使用者，但使用者的選擇由您決定。

   * 設定Elasticsearch：使用者已命名 `magento_elasticsearch` 在此範例中


* `<password file name>` 必須為隱藏的檔案(開頭為 `.`)，且應反映使用者名稱。 如需詳細資訊，請參閱本節稍後的範例。

依照熒幕上的提示為使用者建立密碼。

#### 範例

**範例1： cron**
您必須為cron僅設定一個使用者的驗證；在此範例中，我們使用Web伺服器使用者。 若要為Web伺服器使用者建立密碼檔案，請輸入下列命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**範例2：Elasticsearch**
您必須為兩個使用者設定驗證：一個具有nginx存取權，另一個具有Elasticsearch存取權。 若要為這些使用者建立密碼檔案，請輸入下列命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### 新增其他使用者

若要將另一個使用者新增至您的密碼檔案，請輸入以下命令作為使用者 `root` 許可權：

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### 與Apache的安全通訊

本節探討如何設定 [HTTP基本驗證](https://httpd.apache.org/docs/2.2/howto/auth.html). 同時使用TLS和HTTP基本驗證可防止任何人攔截與Elasticsearch、OpenSearch或您的應用程式伺服器的通訊。

本節探討如何指定可以存取Apache Server的使用者。

1. 使用文字編輯器將下列內容新增至您的安全虛擬主機。

   * Apache 2.4：編輯 `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. 如果您已將前述新增至安全虛擬主機，請移除 `Listen 8080` 和 `<VirtualHost *:8080>` 您先前新增至不安全的虛擬主機的指示。

1. 儲存變更、退出文字編輯器，然後重新啟動Apache：

   * CentOS： `service httpd restart`
   * Ubuntu： `service apache2 restart`

#### 驗證

{{$include /help/_includes/verify-secure-communication.md}}
