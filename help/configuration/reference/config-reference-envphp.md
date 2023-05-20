---
title: env.php參考
description: 請參閱env.php檔案的值清單。
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# env.php參考

此 `env.php` 檔案包含下列區段：

| 名稱 | 說明 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 管理區域的設定 |
| `cache` | 設定Redis頁面和預設快取 |
| `cache_types` | 快取儲存設定 |
| `consumers_wait_for_messages` | 設定使用者如何處理來自訊息佇列的訊息 |
| `cron` | 啟用或停用cron工作 |
| `crypt` | 密碼編譯功能的加密金鑰 |
| `db` | 資料庫連線設定 |
| `default_connection` | 訊息佇列預設連線 |
| `directories` | Commerce目錄對應設定 |
| `downloadable_domains` | 可下載網域清單 |
| `install` | 安裝日期 |
| `lock` | 鎖定提供者設定 |
| `MAGE_MODE` | 此 [應用程式模式](../bootstrap/application-modes.md) |
| `queue` | [訊息佇列](../queues/manage-message-queues.md) 設定 |
| `resource` | 將資源名稱對應到連線 |
| `session` | 工作階段儲存資料 |
| `system` | 停用「 」欄位以在「管理員」中編輯 |
| `x-frame-options` | 設定 [x-frame-options][x-frame-options] |

## 後端

設定 **frontName** 的Commerce管理員url，使用 `backend` env.php中的節點。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## 快取

使用設定redis頁面和預設快取 `cache` 中的節點 `env.php` 檔案。

```conf
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
]
```

進一步瞭解 [Redis設定](../cache/redis-pg-cache.md).

## cache_type

此節點提供所有快取型別設定。

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

深入瞭解不同 [快取型別](../cli/manage-cache.md).

## consumers_wait_for_messages

指定如果處理的訊息數少於，消費者是否應繼續輪詢訊息 `max_messages` 值。 預設值為 `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

下列選項可供使用：

- `1` — 消費者會繼續處理來自訊息佇列的訊息，直到到達 `max_messages` 中指定的值 `env.php` 關閉TCP連線並終止使用者處理序之前的檔案。 如果佇列在到達之前排空 `max_messages` 值，消費者會等待更多訊息到達。

   我們建議大型商戶使用此設定，因為預期訊息流程會持續不變，且不希望處理延遲。

- `0` — 消費者處理佇列中的可用訊息、關閉TCP連線並終止。 即使已處理的訊息數量少於 `max_messages` 中指定的值 `env.php` 檔案。 這有助於防止因訊息佇列處理長時間延遲而導致cron工作發生問題。

   我們建議將此設定用於預期訊息流程不會持續不變且偏好節省運算資源以換取輕微處理延遲的小型商家（因為幾天內沒有訊息）。

## cron

啟用或停用Commerce應用程式的cron工作。 預設會啟用cron工作。 若要停用這些功能，請新增 `cron` 的設定 `env.php` 檔案並將值設定為 `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>當您停用cron工作時，請小心。 當這些變數停用時，Commerce應用程式所需的基本流程將不會執行。

進一步瞭解 [Crons](../cli/configure-cron-jobs.md).

## 加密

Commerce使用加密金鑰來保護密碼和其他敏感資料。 此金鑰會在安裝過程中產生。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

進一步瞭解 [加密金鑰](https://docs.magento.com/user-guide/system/encryption-key.html) 在 _Commerce使用手冊_.

## db

此節點提供所有資料庫組態。

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

定義訊息佇列的預設連線。 值可以是 `db`， `amqp`或自訂佇列系統，例如 `redismq`. 如果您指定任何值，而不是 `db`，必須先安裝並設定message queue軟體。 否則，訊息將無法正確處理。

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

若 `queue/default_connection` 已在系統中指定 `env.php` 檔案，此連線用於透過系統的所有訊息佇列，除非已定義特定連線 `queue_topology.xml`， `queue_publisher.xml` 或 `queue_consumer.xml` 檔案。
例如，如果 `queue/default_connection` 是 `amqp` 在 `env.php` 但 `db` 連線是在模組的佇列組態XML檔案中指定的，模組將使用MySQL做為訊息代理人。

## 目錄

選用的目錄對應選項，在網頁伺服器設定為從提供Commerce應用程式時 `/pub` 目錄 [提升安全性](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

此節點中可用的可下載網域清單。 您可以使用CLI指令來新增、移除或列出其他網域。

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

進一步瞭解 [可下載的網域](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## 安裝

Commerce應用程式的安裝日期。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## 鎖定

鎖定提供者設定是使用 `lock` 節點。

進一步瞭解 [鎖定提供者設定](../../installation/tutorials/lock-provider.md).

## 影像模式

可在此節點中設定部署模式。

```conf
'MAGE_MODE' => 'developer'
```

進一步瞭解 [應用程式模式](../cli/set-mode.md).

## 佇列

此節點提供訊息佇列設定。

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

進一步瞭解 [訊息佇列][message-queue].

## 資源

資源組態設定可在此節點中使用。

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## 工作階段

工作階段設定會儲存在 `session` 節點。

```conf
'session' => [
  'save' => 'files'
],
```

進一步瞭解 [工作階段](../storage/sessions.md).

## x-frame-options

x-frame-options標頭可使用此節點進行設定。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

進一步瞭解 [x-frame-options](../security/xframe-options.md).

## 系統

使用此節點，Commerce會鎖定 `env.php` 然後停用「管理員」中的欄位。

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

進一步瞭解 [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
