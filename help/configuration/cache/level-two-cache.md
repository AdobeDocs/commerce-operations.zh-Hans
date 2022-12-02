---
title: 二级缓存配置
description: 了解如何配置L2缓存。
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 二级缓存配置

缓存可减少远程缓存存储与商务应用程序之间的网络流量。 标准的Commerce实例每个请求传输约300 kb，在某些情况下，流量可能会迅速增加到约1000个请求。

要将网络带宽减少到Redis，请将缓存数据存储在每个Web节点的本地，并将远程缓存用于以下两个目的：

- 检查缓存数据版本，并确保将最新的缓存存储在本地
- 将最新缓存从远程计算机传输到本地计算机

Commerce在Redis中存储经过哈希处理的数据版本，并在后缀“：hash”后附加常规键值。 如果存在过时的本地缓存，则使用缓存适配器将数据传输到本地计算机。

>[!INFO]
>
>对于云基础架构上的Adobe Commerce，您可以使用 [部署变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) ，用于二级缓存配置。

## 配置示例

使用以下示例修改或替换 `app/etc/env.php` 文件。

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
   - `remote_backend` 是远程缓存实施：Redis或MySQL。
   - `remote_backend_options` 是远程缓存配置。
   - `local_backend` 是本地缓存实施： `Cm_Cache_Backend_File`
   - `local_backend_options` 是本地缓存配置。
      - `cache_dir` 是用于存储本地缓存的目录的文件缓存特定选项。
   - `use_stale_cache` 是启用或禁用使用失效缓存的标记。

Adobe建议使用Redis进行远程缓存(`\Magento\Framework\Cache\Backend\Redis`)和 `Cm_Cache_Backend_File` 对于共享内存中数据的本地缓存，使用： `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe建议使用 [`cache preload`](redis-pg-cache.md#redis-preload-feature) 功能，因为它可以极大地减轻Redis的压力。 请不要忘记为预载键添加后缀“：hash”。

## 过时的缓存选项

开始于 [!DNL Commerce] 2.4, `use_stale_cache` 选项在某些情况下可以提高性能。

通常，在性能方面可以接受等待锁的取舍，但商家拥有的块或缓存数越多，等待锁的时间就越长。 在某些情况下，您可以 **键数** \* **查找超时** 流程的时间。 在某些极少数情况下，商户在 `Block/Config` 缓存，因此即使锁的查找超时较小，也可能需要几秒。

过时的缓存仅适用于L2缓存。 如果缓存过时，您可以发送过时的缓存，而新缓存将在并行进程中生成。 要启用过时的缓存，请添加 `'use_stale_cache' => true` 到L2缓存的顶部配置。

Adobe建议启用 `use_stale_cache` 选项，该选项仅适用于从中获益最多的缓存类型，包括：

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

以下代码显示了一个配置示例：

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
