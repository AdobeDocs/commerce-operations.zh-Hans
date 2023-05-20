---
title: 訊息代理人
description: 請依照下列步驟安裝和設定必要的訊息代理程式軟體(例如 [!DNL RabbitMQ])進行內部部署，以安裝Adobe Commerce和Magento Open Source。
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 訊息代理人

Adobe Commerce使用 [!DNL RabbitMQ] 開放原始碼訊息代理人。 它提供可靠、高可用性、可擴充且可攜式的傳訊系統。

訊息佇列提供非同步通訊機制，讓訊息的傳送者與接收者不會相互聯絡。 他們也不需要同時與訊息佇列通訊。 當寄件者將郵件放入佇列時，郵件會儲存到收件者收到郵件為止。

安裝Adobe Commerce或Magento Open Source之前，必須先建立訊息佇列系統。 基本順序為：

1. 安裝 [!DNL RabbitMQ] 以及任何必要條件。
1. Connect [!DNL RabbitMQ] Adobe Commerce或Magento Open Source。

>[!NOTE]
>
>您可以使用MySQL或 [!DNL RabbitMQ] 用於訊息佇列處理。 如需設定訊息佇列系統的詳細資訊，請參閱 [訊息佇列總覽](https://developer.adobe.com/commerce/php/development/components/message-queues/). 如果您搭配Adobe Commerce使用大量API，訊息佇列系統設定預設為使用 [!DNL RabbitMQ] 作為訊息代理人。 另請參閱 [啟動訊息佇列消費者](../../configuration/cli/start-message-queues.md) 以取得詳細資訊。

## 安裝 [!DNL RabbitMQ] 在Ubuntu上

若要安裝 [!DNL RabbitMQ] 在Ubuntu 16上，輸入下列指令：

```bash
sudo apt install -y rabbitmq-server
```

此命令也會安裝必要的Erlang套裝程式。

如果您有舊版Ubuntu， [!DNL RabbitMQ] 建議從他們的網站安裝套件。

1. 從下載.deb套件 [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. 使用安裝套件 `dpkg`.

請參閱 [在Debian/Ubuntu上安裝](https://www.rabbitmq.com/install-debian.html) 以取得詳細資訊。

## 安裝 [!DNL RabbitMQ] 在CentOS上

### 安裝Erlang

[!DNL RabbitMQ] 是使用Erlang程式設計語言撰寫的，必須安裝在與 [!DNL RabbitMQ].

另請參閱 [手動安裝](https://www.erlang-solutions.com/downloads/) 以取得詳細資訊。

請參閱 [[!DNL RabbitMQ]/Erlang版本對照表](https://www.rabbitmq.com/which-erlang.html) 以安裝正確的版本。

### 安裝 [!DNL RabbitMQ]

此 [!DNL RabbitMQ] 伺服器包含在CentOS上，但版本通常較舊。 [!DNL RabbitMQ] 建議從他們的網站安裝套件。

請參閱 [!DNL RabbitMQ] 安裝頁面以取得最新支援的版本。 Adobe Commerce和Magento Open Source2.3和2.4支援 [!DNL RabbitMQ] 3.8.x.

請參閱 [在RPM Linux上進行安裝](https://www.rabbitmq.com/install-rpm.html) 以取得詳細資訊。

## 設定 [!DNL RabbitMQ]

檢閱正式檔案 [!DNL RabbitMQ] 設定和管理檔案 [!DNL RabbitMQ]. 請注意下列專案：

* 環境變數
* 連線埠存取
* 預設使用者帳戶
* 啟動和停止代理人
* 系統限制

## 安裝方式 [!DNL RabbitMQ] 並連線

如果您安裝Adobe Commerce或Magento Open Source _晚於_ 您安裝 [!DNL RabbitMQ]，請在安裝期間新增下列命令列引數：

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

其中：

| 引數 | 說明 |
|--- |--- |
| `--amqp-host` | 主機名稱，其中 [!DNL RabbitMQ] 已安裝。 |
| `--amqp-port` | 用來連線的連線埠 [!DNL RabbitMQ]. 預設值為 `5672`. |
| `--amqp-user` | 用於連線到的使用者名稱 [!DNL RabbitMQ]. 不要使用預設使用者 `guest`. |
| `--amqp-password` | 用於連線的密碼 [!DNL RabbitMQ]. 不要使用預設密碼 `guest`. |
| `--amqp-virtualhost` | 用於連線的虛擬主機 [!DNL RabbitMQ]. 預設值為 `/`. |
| `--amqp-ssl` | 指示是否連線到 [!DNL RabbitMQ]. 預設值為 `false`. 如果您將值設為true，請參閱設定SSL以取得詳細資訊。 |

## Connect [!DNL RabbitMQ]

如果您已安裝Adobe Commerce或Magento Open Source，而且您想要將其連線至 [!DNL RabbitMQ]，新增 `queue` 中的區段 `<install_directory>/app/etc/env.php` 檔案，使其類似於以下內容：

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

您也可以設定 [!DNL RabbitMQ] 設定值使用 `bin/magento setup:config:set` 命令：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

執行命令或更新 `<install_directory>/app/etc/env.php` 具有AMQP設定值的檔案，執行 `bin/magento setup:upgrade` 以套用變更，並建立所需的佇列和交換 [!DNL RabbitMQ].

## 設定SSL

若要設定SSL支援，請編輯 `ssl` 和 `ssl_options` 中的引數 `<install_directory>/app/etc/env.php` 檔案，以便它們類似於以下內容：

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## 啟動訊息佇列消費者

連線Adobe Commerce和之後 [!DNL RabbitMQ]，您必須啟動訊息佇列取用者。 另請參閱 [設定訊息佇列](../../configuration/cli/start-message-queues.md) 以取得詳細資訊。
