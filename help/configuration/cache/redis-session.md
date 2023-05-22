---
title: 將Redis用於工作階段儲存
description: 瞭解如何為工作階段儲存設定Redis。
feature: Configuration, Cache
exl-id: f93f500d-65b0-4788-96ab-f1c3d2d40a38
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 1%

---

# 將Redis用於工作階段儲存

>[!IMPORTANT]
>
>您必須 [安裝Redis](config-redis.md#install-redis) 然後再繼續。


Commerce現在提供命令列選項來設定Redis工作階段存放區。 在舊版中，您已編輯 `<Commerce install dir>app/etc/env.php` 檔案。 命令列會提供驗證，且是建議的設定方法，但您仍可編輯 `env.php` 檔案。

執行 `setup:config:set` 命令並指定Redis特定引數。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

位置

`--session-save=redis` 啟用Redis工作階段儲存。 如果已啟用此功能，請省略此引數。

`--session-save-redis-<parameter_name>=<parameter_value>` 是設定工作階段存放區的引數/值組清單：

| 命令列引數 | 引數名稱 | 含義 | 預設值 |
|--- |--- |--- |--- |
| session-save-redis-host | 主機 | 完整的主機名稱、IP位址或絕對路徑（如果使用UNIX通訊端）。 | localhost |
| session-save-redis-port | 連線埠 | Redis伺服器接聽連線埠。 | 6379 |
| session-save-redis-password | 密碼 | 如果Redis伺服器需要驗證，請指定密碼。 | 空白 |
| session-save-redis-timeout | 逾時 | 連線逾時（秒）。 | 2.5 |
| session-save-redis-persistent-id | persistent_identifier | 啟用持續連線的唯一字串（例如sess-db0）。<br>[phpredis和php-fpm的已知問題](https://github.com/phpredis/phpredis/issues/70). |
| session-save-redis-db | 資料庫 | 唯一的Redis資料庫編號，建議用來防止資料遺失。<br><br>**重要**：如果您將Redis用於多種型別的快取，則資料庫編號必須不同。 建議您將預設快取資料庫編號指派為0，將分頁快取資料庫編號指派為1，並將工作階段儲存資料庫編號指派為2。 | 0 |
| session-save-redis-compression-threshold | compression_threshold | 設為0可停用壓縮(建議在 `suhosin.session.encrypt = On`)。<br>[字串超過64 KB的已知問題](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18). | 2048 |
| session-save-redis-compression-lib | compression_library | 選項： gzip、lzf、lz4或snappy。 | gzip |
| session-save-redis-log-level | log_level | 設定為下列任一專案，依從最詳細到最詳細順序列出：<ul><li>0 （緊急：只有最嚴重的錯誤）<li>1 （警示：需要立即動作）<li>2 （嚴重：應用程式元件無法使用）<li>3 （錯誤：執行階段錯誤，非嚴重，但必須監控）<li>4 （警告：其他資訊，建議使用）<li>5 （注意：正常但重要的條件）<li>6 （資訊：資訊訊息）<li>7 （除錯：僅供開發或測試使用的最多資訊）</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | 可等待鎖定一個工作階段的最大處理序數目。 對於大型生產叢集，請將此項設定為至少PHP流程數量的10%。 | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | 嘗試解除前端（亦即storefront）工作階段鎖定之前的等待秒數。 | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | 嘗試解除對Admin HTML （即管理員）工作階段的鎖定前等待的秒數。 | 30 |
| session-save-redis-first-lifetime | first_lifetime | 非機器人在第一次寫入時的工作階段期限（以秒為單位），或使用0來停用。 | 600 |
| session-save-redis-bot-first-lifetime | bot_first_lifetime | 機器人第一次寫入工作階段的期限（以秒為單位），或使用0來停用。 | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | 機器人後續寫入作業的工作階段期限（以秒為單位），或使用0加以停用。 | 7200 |
| session-save-redis-disable-locking | disable_locking | 完全停用工作階段鎖定。 | 0 （假） |
| session-save-redis-min-lifetime | min_lifetime | 工作階段存留期下限（以秒為單位）。 | 60 |
| session-save-redis-max-lifetime | max_lifetime | 工作階段期限上限（以秒為單位）。 | 2592000 （720小時） |
| session-save-redis-sentinel-master | sentinel_master | Redis Sentinel主名稱 | 空白 |
| session-save-redis-sentinel-servers | sentinel_servers | Redis Sentinel伺服器清單（以逗號分隔） | 空白 |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | 驗證Redis Sentinel主要狀態旗標 | 0 （假） |
| session-save-redis-sentinel-connect-retries | sentinel_connect_retries | Sentinels的連線重試 | 5 |

## 範例

下列範例會將Redis設為工作階段資料存放區，並將主機設為 `127.0.0.1`，將記錄層級設為4，並將資料庫編號設為2。 所有其他引數都會設定為預設值。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 結果

Commerce會將類似下列的行新增至 `<magento_root>app/etc/env.php`：

```php
    'session' =>
    array (
      'save' => 'redis',
      'redis' =>
      array (
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000'
      )
    ),
```

>[!INFO]
>
>工作階段記錄的TTL會使用Cookie期限的值，此值是在Admin中設定。 如果「Cookie期限」設為0 （預設為3600），則Redis工作階段會在min_lifetime中指定的秒數內到期（預設為60）。 這種差異是因為Redis和工作階段Cookie解讀期限值0的方式有所差異。 如果不需要該行為，請增加min_lifetime的值。

## 驗證Redis連線

若要確認Redis與Commerce是否共同運作，請登入執行Redis的伺服器、開啟終端機，並使用Redis監視命令或ping命令。

### Redis監視命令

```bash
redis-cli monitor
```

工作階段儲存輸出範例：

```terminal
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Redis ping指令

```bash
redis-cli ping
```

`PONG` 應為回應。

如果兩個命令都成功，Redis就會正確設定。

### 檢查壓縮資料

若要檢查壓縮的工作階段資料和頁面快取，請 [RESP.app](https://flathub.org/apps/details/app.resp.RESP) 支援自動解壓縮Commerce 2工作階段和頁面快取，並以人類可讀的格式顯示PHP工作階段資料。
