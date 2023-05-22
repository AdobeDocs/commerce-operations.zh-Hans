---
title: L2快取設定
description: 瞭解如何設定L2快取。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# L2快取設定

快取可減少遠端快取儲存與Commerce應用程式之間的網路流量。 標準Commerce執行個體會針對每個請求傳輸約300 kb的流量，而流量在某些情況下可能會快速增加至超過~1000個請求。

若要減少Redis的網路頻寬，請將快取資料儲存在每個網頁節點本機，並使用遠端快取有兩個用途：

- 檢查快取資料版本，並確定最新的快取儲存在本機
- 將最新的快取從遠端電腦傳輸至本機電腦

Commerce會將雜湊資料版本儲存在Redis中，並在一般索引鍵後面附加尾碼「：hash」。 如果有過時的本機快取，資料會透過快取轉接器傳輸到本機電腦。

>[!INFO]
>
>對於雲端基礎結構上的Adobe Commerce，您可以使用 [部署變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 用於L2快取設定。

## 設定範例

使用下列範例來修改或取代中現有的快取區段 `app/etc/env.php` 檔案。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => false,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

其中：

- `backend` 是L2快取實作。
- `backend_options` 是L2快取設定。
   - `remote_backend` 是遠端快取實作： Redis或MySQL。
   - `remote_backend_options` 是遠端快取設定。
   - `local_backend` 是本機快取實作： `Cm_Cache_Backend_File`
   - `local_backend_options` 是本機快取設定。
      - `cache_dir` 是儲存本機快取之目錄的檔案快取特定選項。
   - `use_stale_cache` 是啟用或停用使用過時快取的標幟。

Adobe建議使用Redis進行遠端快取(`\Magento\Framework\Cache\Backend\Redis`)和 `Cm_Cache_Backend_File` 對於共用記憶體中資料的本機快取，使用： `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe建議使用 [`cache preload`](redis-pg-cache.md#redis-preload-feature) 特徵，因為它大幅降低Redis上的壓力。 別忘了為預先載入金鑰新增尾碼&#39;：hash&#39;。

## 過時的快取選項

開始使用 [!DNL Commerce] 2.4， `use_stale_cache` 選項可改善某些特定情況下的效能。

一般而言，效能方面可接受鎖定等待的折衷，但商家擁有的「區塊」或「快取」數目越多，等待鎖的時間就越多。 在某些情況下，您可以等待 **金鑰數目** \* **查詢逾時** 處理序的時間長度。 在少數情況下，商家可能會有數百個金鑰 `Block/Config` 快取，因此即使是鎖定的小型查閱逾時也可能需要幾秒鐘的時間。

過時的快取僅適用於L2快取記憶體。 使用過時的快取記憶體，您可以傳送過時的快取，而在平行程式中產生新的快取。 若要啟用過時的快取，請新增 `'use_stale_cache' => true` 到L2快取的頂端設定。

Adobe建議啟用 `use_stale_cache` 選項僅適用於從中獲益最多的快取型別，包括：

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

下列程式碼顯示設定範例：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => false,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => true,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled']
    ],
],
```
