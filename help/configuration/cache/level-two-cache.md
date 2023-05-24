---
title: 二级缓存配置
description: 了解如何配置L2缓存。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# 二级缓存配置

缓存可减少远程缓存存储和Commerce应用程序之间的网络流量。 标准Commerce实例会为每个请求传输大约300 kb的流量，在某些情况下，流量可能会迅速增长到超过1000个请求。

要减少Redis的网络带宽，请将缓存数据存储到本地的每个Web节点上，并将远程缓存用于两个目的：

- 检查缓存数据版本，并确保最新的缓存存储在本地
- 将最新的缓存从远程计算机传输到本地计算机

Commerce将经过哈希处理的数据版本存储在Redis中，并在常规键后面附加后缀“：hash”。 如果存在过时的本地缓存，则会使用缓存适配器将数据传输到本地计算机。

>[!INFO]
>
>对于云基础架构上的Adobe Commerce，您可以使用 [部署变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 二级缓存配置。

## 配置示例

使用以下示例修改或替换中的现有缓存部分 `app/etc/env.php` 文件。

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

- `backend` 是L2缓存实施。
- `backend_options` 是L2缓存配置。
   - `remote_backend` 是远程缓存实施： Redis或MySQL。
   - `remote_backend_options` 是远程缓存配置。
   - `local_backend` 是本地缓存实施： `Cm_Cache_Backend_File`
   - `local_backend_options` 是本地缓存配置。
      - `cache_dir` 是存储本地缓存的目录的文件缓存特定选项。
   - `use_stale_cache` 是一个标志，用于启用或禁用过时的缓存。

Adobe建议使用Redis进行远程缓存(`\Magento\Framework\Cache\Backend\Redis`)和 `Cm_Cache_Backend_File` 对于共享内存中数据的本地缓存，使用： `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe建议使用 [`cache preload`](redis-pg-cache.md#redis-preload-feature) 特征，因为它极大地降低了对Redis的压力。 不要忘记为预加载密钥添加后缀“：hash”。

## 过时的缓存选项

开始使用 [!DNL Commerce] 2.4， `use_stale_cache` 选项可以提高某些特定情况下的性能。

通常，从性能方面来说，与锁定等待的折衷是可以接受的，但商家拥有的Block或Cache数量越多，等待锁的时间就越多。 在某些情况下，您可以等待 **键数** \* **查找超时** 处理所需的时间。 在极少数情况下，商户可能拥有数百把钥匙 `Block/Config` 缓存，因此，即使锁的查找超时时间很短，也可能需要几秒钟。

过时的缓存仅适用于二级缓存。 使用过时的缓存，您可以发送过时的缓存，而在并行进程中生成新的缓存。 要启用过时的缓存，请添加 `'use_stale_cache' => true` 到L2缓存的顶部配置。

Adobe建议启用 `use_stale_cache` 选项仅适用于从中获益最多的缓存类型，包括：

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

以下代码显示了一个示例配置：

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
