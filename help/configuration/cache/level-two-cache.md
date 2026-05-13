---
title: 用于性能优化的二级缓存配置
description: 了解如何在Adobe Commerce中配置二级缓存以减少网络流量并提高性能。 了解旧版和Symfony实施选项。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: 605b2e59d200bc8eeab43e91006a3f95e6a6c138
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---

# 用于性能优化的二级缓存配置

L2（两级）缓存通过在每个Web节点上添加本地缓存层，减少了远程缓存存储（Redis或Valkey）与Commerce应用程序之间的网络流量。 每个请求的标准Commerce实例传输大约300 KB，在某些情况下，流量可能会快速增长到1000多个请求。

通过二级缓存，每个Web节点将经常访问的数据存储在本地，并将远程缓存用于两个目的：

- 检查缓存数据版本，确保最新的缓存存储在本地
- 正在将更新的缓存数据从远程存储传输到本地计算机

Commerce会将经过哈希处理的数据版本存储在远程缓存中，并将后缀`:hash`附加到常规键中。 当本地缓存过期时，将通过缓存适配器从远程计算机中获取数据。

有两种可用的二级缓存实施：

| 实现 | 版本 | 描述 |
| -------------- | ------- | ----------- |
| [旧版(`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | 2.4.x | 基于Zend的二级缓存，具有`Cm_Cache_Backend_File`用于本地存储 |
| [现代(`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | 基于Symfony缓存的L2具有PSR-6合规性和增强的性能 |

>[!INFO]
>
>对于云基础架构上的Adobe Commerce，您可以使用[部署变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hans#redis_backend)来配置二级缓存。

## 旧版L2缓存配置(RemoteSynchronizedCache)

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

从Commerce 2.4开始，`use_stale_cache`选项通过在并行进程中生成新缓存数据时提供以前缓存的数据，可以在特定情况下提高性能。

通常，从性能角度来看，锁定等待的权衡是可以接受的。 但是，随着块数或缓存条目的增加，锁定需要更多时间。 在某些情况下，等待时间最多可以为进程的&#x200B;**键数** x **查找超时**。 在极少数情况下，商家的`Block/Config`缓存中可能有数百个键，因此，即使是较小的锁查找超时也可能需要几秒钟。

>[!IMPORTANT]
>
>过时的缓存仅适用于二级缓存。 要启用它，请将`'use_stale_cache' => true`添加到二级缓存前端的最上层配置中。

Adobe建议仅对从中获益最大的缓存类型启用`use_stale_cache`选项，包括：

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe不建议为`default`缓存类型启用`use_stale_cache`选项。

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

## 现代Symfony L2缓存实施

[!BADGE 2.4.9-beta]{type=Negative tooltip="仅在2.4.9 Beta版中提供。"}

从Commerce 2.4.9开始，您可以使用基于Symfony缓存的二级缓存实现（`symfony_l2`后端），该实现提供了新型、符合PSR-6的缓存实现，其性能比传统`RemoteSynchronizedCache`有显着改进。

### Symfony二级缓存的优势

- **现代体系结构**：基于Symfony缓存组件构建（符合PSR-6）
- **更好的性能**：对Igbinary序列化、gzip压缩和Lua脚本的本机支持
- **永久连接**：通过连接池减少Redis或Valkey连接开销
- **预加载密钥**：支持为关键数据预加载缓存密钥
- **过时缓存支持**：与`use_stale_cache`选项完全兼容
- **简化的配置**：清理器后端类型名称(`redis`、`valkey`、`file`)

### Symfony L2缓存的配置示例

为L2缓存使用简化的`symfony_l2`后端类型：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Redis with Symfony Cache
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                    'preload_keys' => [
                        'prefix_EAV_ENTITY_TYPES:hash',
                        'prefix_GLOBAL_PLUGIN_LIST:hash',
                        'prefix_DB_IS_UP_TO_DATE:hash',
                        'prefix_SYSTEM_DEFAULT:hash',
                    ],
                ],
                // L1 (Local): File cache
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
                'cleanup_percentage' => 90,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

### Symfony L2缓存和过时的缓存

配置单独的前端以支持过时的缓存：

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
            ],
        ],
        // Stale cache enabled frontend
        'stale_cache_enabled' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_stale',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1_stale'
                ],
                'use_stale_cache' => true,
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
        'translate' => ['frontend' => 'stale_cache_enabled'],
    ],
],
```

### Symfony L2缓存的后端选项

| 选项 | 类型 | 默认 | 描述 |
|--------|------|---------|-------------------------------------------------------------------|
| `remote_backend` | 字符串 | `'redis'` | 远程后端类型： `redis`、`valkey`或`file` |
| `remote_backend_options` | 数组 | `[]` | 远程后端配置（请参阅Redis/Valkey文档） |
| `local_backend` | 字符串 | `'file'` | 本地后端类型： `file`或`apcu` |
| `local_backend_options` | 数组 | `[]` | 本地后端配置 |
| `cleanup_percentage` | 整数 | `90` | 一级缓存清理阈值(1-100) |
| `use_stale_cache` | 布尔型 | `false` | 启用过时缓存以实现高可用性 |

### Valkey支持

`symfony_l2`后端还支持将Valkey作为远程后端：

```php
'backend_options' => [
    'remote_backend' => 'valkey',  // Use Valkey instead of Redis
    'remote_backend_options' => [
        'server' => 'localhost',
        'database' => '0',
        'port' => '6379',
        'serializer' => 'igbinary',
        'compression_lib' => 'gzip',
    ],
    // ... rest of configuration
]
```

有关详细的配置选项，请参阅：
- [使用Symfony缓存配置Redis缓存](redis-pg-cache.md)
- [使用Symfony缓存配置Valkey缓存](valkey-pg-cache.md)
