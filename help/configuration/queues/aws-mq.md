---
title: 設定Amazon訊息佇列
description: 瞭解如何設定Commerce以使用AWS MQ服務。
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# 設定Amazon訊息佇列

自Commerce 2.4.3起，Amazon Message Queue (MQ)可取代雲端就緒，供內部部署訊息佇列例項使用。

若要在AWS上建立訊息佇列，請參閱 [設定Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) 在 _AWS檔案_.

## 設定AWS MQ的Commerce

若要連線至AWS MQ服務，請設定 `queue.amqp` 中的物件 `env.php` 檔案。
AWS訊息佇列需要SSL/TLS連線。

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

其中：

- `host`—AMQP端點的URL；按一下AWS中的代理人名稱即可使用(移除「https://」和尾端連線埠號碼)
- `user` — 建立AWS MQ Broker時輸入的使用者名稱值
- `password` — 建立AWS MQ Broker時輸入的密碼值

>[!INFO]
>
>Amazon MQ僅支援TLS連線。 不支援對等驗證。

編輯後 `env.php` 檔案，執行以下命令以完成設定：

```bash
bin/magento setup:upgrade
```

## Commerce如何使用AWS MQ服務

此 `async.operations.all` 訊息佇列消費者使用AMQP連線。

此消費者會路由任何前置詞為的主題名稱 `async` 透過AWS MQ連線。

例如，在 `InventoryCatalog` 有：

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

的預設設定 `InventoryCatalog` 不會將訊息發佈至 [!DNL RabbitMQ]；預設行為是在相同的使用者執行緒中執行動作。 判斷 `InventoryCatalog` 若要發佈訊息，請啟用 `cataloginventory/bulk_operations/async`. 從管理員，前往 **商店** >設定> **目錄** > **詳細目錄** >管理員大量作業和設定  `Run asynchronously`至 **是**.

## 測試訊息佇列

若要測試從Commerce傳送至的訊息 [!DNL RabbitMQ]：

1. 登入 [!DNL RabbitMQ] AWS中的Web主控台，用於監視佇列。
1. 在「管理員」中建立產品。
1. 建立「庫存管理系統」來源。
1. 啟用 **商店** >設定> **目錄** > **詳細目錄** >管理員大量作業>非同步執行。
1. 前往 **目錄** >產品。 從格線中，選取上面建立的產品，然後按一下 **指定存貨來源**.
1. 按一下 **儲存並關閉** 以完成程式。

   您現在應該會看到訊息出現在 [!DNL RabbitMQ] 網頁主控台。

1. 開始 `async.operations.all` 訊息佇列消費者。

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

您現在應該會在中看到已佇列訊息已處理 [!DNL RabbitMQ] 網頁主控台。
在「管理員」中確認產品上的詳細目錄來源已變更。
