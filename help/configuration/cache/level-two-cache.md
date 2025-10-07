---
title: 二级缓存配置
description: 了解如何配置二级缓存以优化Adobe Commerce性能。 了解设置步骤和网络流量减少技术。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# 二级缓存配置

通过缓存，可以降低远程缓存存储和Commerce应用程序之间的网络流量。 标准Commerce实例每次请求传输约300 kb，在某些情况下，流量可能会快速增长到超过1000个请求。

要减少Redis的网络带宽，请将缓存数据本地存储在每个Web节点上，并将远程缓存用于两个目的：

- 检查缓存数据版本，并确保最新的缓存存储在本地
- 将最新缓存从远程计算机传输到本地计算机

Commerce将经过哈希处理的数据版本存储在Redis中，后缀“:hash”附加到常规键中。 如果存在过时的本地缓存，则会使用缓存适配器将数据传输到本地计算机。

>[!INFO]
>
>对于云基础架构上的Adobe Commerce，您可以使用[部署变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hans#redis_backend)来配置二级缓存。

## 配置示例

使用以下示例修改或替换`app/etc/env.php`文件中的现有缓存部分。

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
                ]
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

- `backend`是二级缓存实现。
- `backend_options`是二级缓存配置。
   - `remote_backend`是远程缓存实现： Redis或MySQL。
   - `remote_backend_options`是远程缓存配置。
   - `local_backend`是本地缓存实现： `Cm_Cache_Backend_File`
   - `local_backend_options`是本地缓存配置。
   - `cache_dir`是用于存储本地缓存的目录的文件缓存特定选项。

Adobe建议使用Redis进行远程缓存(`\Magento\Framework\Cache\Backend\Redis`)，使用`Cm_Cache_Backend_File`进行共享内存中数据的本地缓存，使用： `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe建议使用[`cache preload`](redis-pg-cache.md#redis-preload-feature)功能，因为它可显着降低Redis上的压力。 不要忘记为预加载密钥添加后缀“:hash”。

## 过时的缓存选项

从[!DNL Commerce] 2.4开始，`use_stale_cache`选项可以在某些特定情况下提高性能。

通常，从性能方面来说，与等待锁的折衷是可以接受的，但商家拥有的块或缓存的数目越大，等待锁的时间就越多。 在某些情况下，您可以等待&#x200B;**个键** \* **查找超时**&#x200B;时间来处理该进程。 在极少数情况下，商家的`Block/Config`缓存中可能有数百个密钥，因此即使是较小的锁定查找超时也可能需要几秒钟。

过时的缓存仅适用于二级缓存。 使用过时的缓存，您可以发送过时的缓存，同时在并行进程中生成新的缓存。 要启用过时的缓存，请将`'use_stale_cache' => true`添加到L2缓存的顶部配置中。

Adobe建议仅对从中获益最大的缓存类型启用`use_stale_cache`选项，包括：

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe不建议为`use_stale_cache`缓存类型启用`default`选项。

以下代码显示了示例配置：

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
                ]
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
