---
title: Redis服務設定的最佳實務
description: 瞭解如何使用Adobe Commerce的延伸Redis快取實作來改善快取效能。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Redis服務設定的最佳實務

- 使用延伸的Redis快取實作，其中包括下列最佳化，以將對來自Adobe Commerce的每個請求執行的Redis查詢數量降至最低：
   - 減少Redis和Adobe Commerce之間的網路資料傳輸大小
   - 改善介面卡自動判斷需要載入哪些內容的能力，以降低CPU週期的Redis耗用量
   - 減少Redis寫入作業的競爭條件
- 將Redis快取與Redis工作階段分開
- 壓縮Redis快取並使用 `gzip` 提升效能

## 延伸的Redis快取實作

更新您的設定以使用延伸的Redis快取實作 `\Magento\Framework\Cache\Backend\Redis`.

### 設定雲端部署

設定Redis快取，方法是 `REDIS_BACKEND` 中的部署變數 `.magento.env.yaml` 設定檔。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

如需詳細資訊，請參閱 [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 中的變數說明 _雲端基礎結構上的Commerce指南_.

>[!NOTE]
>
> 檢查 `ece-tools` 版本，從命令列安裝到您的本機環境中，使用 `composer show magento/ece-tools` 命令。 如有需要， [更新至最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>執行 _not_ 使用設定雲端基礎結構專案的Redis從屬連線 [縮放架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). 這會導致Redis連線錯誤。 另請參閱 [Redis設定指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 在 _雲端基礎結構上的Commerce_ 指南。

### 設定內部部署

針對Adobe Commerce內部部署，請使用設定新的Redis快取實作 `bin/magento:setup` 命令。 如需指示，請參閱 [預設快取使用Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## 分隔快取與工作階段執行個體

將Redis快取與Redis工作階段分開可讓您獨立管理快取和工作階段，以防止快取問題影響工作階段。

1. 更新 `.magento/services.yaml` 設定檔。

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
      type: redis:6.0
   
   search:
      type: elasticsearch:7.9
      disk: 5000
   
   rabbitmq:
      type: rabbitmq:3.8
      disk: 2048
   ```

1. 更新 `.magento.app.yaml` 設定檔。

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 提交 [Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 變更Pro生產和中繼環境上的Redis服務設定。 包含更新的 `.magento/services.yaml` 和 `.magento.app.yaml` 組態檔。

1. 確認新執行個體正在執行，並記下連線埠號碼。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 將連線埠號碼新增至 `.magento.env.yaml` 設定檔。

   >[!NOTE]
   >`disable_locking` 必須設定為 `1`.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. 從移除工作階段 [預設資料庫](../../../configuration/cache/redis-pg-cache.md) (`db 0`)。

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

部署期間，您應該會在 [建置和部署記錄](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs)：

```terminal
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## 快取壓縮

使用快取壓縮，但請注意，使用者端效能是有代價的。 如果您有備用CPU，請啟用它。 另請參閱 [將Redis用於工作階段儲存](../../../configuration/cache/redis-session.md).

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## 其他資訊

- [Redis頁面快取](../../../configuration/cache/redis-pg-cache.md)
- [將Redis用於工作階段儲存](../../../configuration/cache/redis-session.md)
