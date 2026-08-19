---
title: 用于性能优化的二级缓存配置
description: 了解如何在Adobe Commerce中配置二级缓存以减少网络流量并提高性能。 了解旧版和Symfony实施选项。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce内部部署项目。"
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 7ebadd26eee51aa2c2f3dfe8a8a2ed3dc20657b9
workflow-type: tm+mt
source-wordcount: 1725
ht-degree: 0%

---

# 用于性能优化的二级缓存配置

L2（两级）缓存通过在每个Web节点上添加本地缓存层，减少了远程缓存存储（Redis或Valkey）与Commerce应用程序之间的网络流量。 每个请求的标准Commerce实例传输大约300 KB，在某些情况下，流量可能会快速增长到1000多个请求。

通过二级缓存，每个Web节点将经常访问的数据存储在本地，并将远程缓存用于两个目的：

- 检查缓存数据版本，确保最新的缓存存储在本地
- 正在将更新的缓存数据从远程存储传输到本地计算机

Commerce会将经过哈希处理的数据版本存储在远程缓存中，并将后缀`:hash`附加到常规键中。 当本地缓存过期时，将通过缓存适配器从远程计算机中获取数据。

Adobe Commerce中有两种可用的二级缓存实施：

| 实现 | 版本 | 描述 |
| -------------- | ------- | ----------- |
| [旧版(`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | 基于Zend的二级缓存，具有`Cm_Cache_Backend_File`用于本地存储 |
| [现代(`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | 基于Symfony缓存的L2具有PSR-6合规性和增强的性能。 支持Valkey。 |

Symfony L2缓存是Adobe Commerce 2.4.9及更高版本的推荐实施。 它提供了一种符合PSR-6标准的现代化缓存实现，与传统`RemoteSynchronizedCache`相比，具有显着的性能改进。

## 旧版L2缓存配置(RemoteSynchronizedCache)

旧版二级缓存配置说明适用于旧版Adobe Commerce。 如果您使用的是Adobe Commerce版本2.4.9或更高版本，请将Valkey与[Modern Symfony L2缓存实现](#modern-symfony-l2-cache-implementation)一起使用。

>[!NOTE]
>
>本页仅介绍内部部署配置。 对于云上的Adobe Commerce，请参阅[配置二级缓存](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache)。

对于支持Redis的Adobe Commerce本地版本，请使用以下示例修改或替换`app/etc/env.php`文件中的现有缓存部分。

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
]
```

其中：

- `backend`是二级缓存实现。
- `backend_options`是二级缓存配置。
  - `remote_backend`是远程缓存实现： Redis或MySQL。
  - `remote_backend_options`是远程缓存配置。
  - `local_backend`是本地缓存实现： `Cm_Cache_Backend_File`。
  - `local_backend_options`是本地缓存配置。
  - `cache_dir`是用于存储本地缓存的目录的文件缓存特定选项。

对于支持Redis的2.4.9之前的Adobe Commerce版本，Adobe建议使用Redis进行远程缓存(`\Magento\Framework\Cache\Backend\Redis`)，并使用`Cm_Cache_Backend_File`在共享内存中本地缓存数据，具体方法是： `'local_backend_options' => ['cache_dir' => '/dev/shm/']`。

Adobe建议使用[`cache preload`](redis-pg-cache.md#redis-preload-feature)功能，因为它可显着降低Redis上的压力。 不要忘记为预加载密钥添加后缀`:hash`。

## 过时的缓存选项

从Commerce 2.4开始，`use_stale_cache`选项通过在并行进程中生成新缓存数据时提供以前缓存的数据，可以在特定情况下提高性能。 本节中介绍的建议缓存类型和权衡适用于旧版`RemoteSynchronizedCache`和`symfony_l2`实施。 有关`symfony_l2`配置示例，请参阅[Symfony L2缓存和过时的缓存](#symfony-l2-cache-with-stale-cache)。

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

以下代码显示了旧版`RemoteSynchronizedCache`后端的示例配置。 有关`symfony_l2`示例，请参阅[Symfony L2缓存和过时的缓存](#symfony-l2-cache-with-stale-cache)。

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

在Commerce版本2.4.9+中，使用基于Symfony缓存的二级缓存实现（`symfony_l2`后端），而不是旧的二级缓存。 Symfony L2缓存提供了符合PSR-6标准的现代化缓存实现，与传统`RemoteSynchronizedCache`相比，性能有了显着改进。

>[!IMPORTANT]
>
>Redis不支持作为远程缓存后端，其开头为：
>
>- Adobe Commerce 2.4.9及更高版本
>- 2.4.8-p4及更高版本的修补程序
>- 2.4.7-p9及更高版本的修补程序
>- 2.4.6-p14及更高版本的修补程序
>- 2.4.5-p16及更高版本的修补程序
>
>如果升级超过这些版本，请设置Valkey并更新缓存配置以使用`symfony_l2`。 请参阅[设置Valkey](config-valkey.md)和[系统要求](../../installation/system-requirements.md)。

### Symfony二级缓存的优势

- **现代体系结构：**&#x200B;基于Symfony缓存组件构建（符合PSR-6）
- **更好的性能：**&#x200B;对Igbinary序列化、gzip压缩和Lua脚本的本机支持
- **永久连接：**&#x200B;减少了连接池的Valkey连接开销
- **预加载键：**&#x200B;支持关键数据的缓存键预加载
- **过时缓存支持：**&#x200B;与`use_stale_cache`选项完全兼容
- **简化的配置：**&#x200B;清理器后端类型名称(`valkey`，`file`)

### 从RemoteSynchronizedCache迁移到Symfony L2

如果您要将内部部署安装从旧版`RemoteSynchronizedCache`后端升级到`symfony_l2`，请在更新`app/etc/env.php`之前查看以下内容。 仅更改`backend`值是不够的。 配置结构、键名和某些默认行为各不相同。

- **配置结构已更改。** `remote_backend`、`remote_backend_options`和`local_backend`在`symfony_l2`下使用不同的值。 例如，`remote_backend`变为`'valkey'`而不是完全限定的类名。 使用下面的[配置示例](#configuration-example-with-symfony-l2-cache)作为您的起点，而不是就地编辑您现有的旧配置。

- 不建议将&#x200B;**`preload_keys`与`symfony_l2`.**&#x200B;一起使用 如果您的旧版配置包含`preload_keys`，请在迁移过程中将其删除。 预加载密钥不会提高`symfony_l2`下的性能，并且会触发其他不必要的密钥查找，从而增加Valkey的负载。

- **压缩需要一个显式标志。** 仅设置`compression_lib`不会在`symfony_l2`下启用压缩。 有关所需的`compress_data`设置，请参阅Symfony L2缓存的[后端选项](#backend-options-for-symfony-l2-cache)。

- 对于手动配置的内部部署，默认情况下不启用&#x200B;**过时缓存。** `symfony_l2`下的`use_stale_cache`默认为`false`（请参阅[后端选项表](#backend-options-for-symfony-l2-cache)）。 如果您的旧版配置使用了`stale_cache_enabled`前端，则必须使用[Symfony L2缓存中的模式显式重新创建它，该模式具有过时的缓存](#symfony-l2-cache-with-stale-cache)。

>[!NOTE]
>
>设置`VALKEY_BACKEND: symfony_l2`部署变量的云环境上的Adobe Commerce具有由`ece-tools`自动生成的完整L2配置，包括`stale_cache_enabled`前端。 请参阅[配置Symfony L2缓存](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)以了解特定于云的行为。

- **Redis不是`symfony_l2`支持的远程后端。** 作为此更改的一部分，请迁移到Valkey。 请参阅[设置Valkey](config-valkey.md)。

### Symfony L2缓存的配置示例

>[!NOTE]
>
>此示例适用于本地`app/etc/env.php`配置。 对于Adobe Commerce on Cloud，缓存配置由`ece-tools`自动管理。 请参阅[配置Symfony L2缓存](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)，而不是直接编辑`env.php`。

在`app/etc/env.php`文件中，为L2缓存使用简化的`symfony_l2`后端类型。 此示例不包括`preload_keys`配置，不建议对`symfony_l2`使用此配置。 有关详细信息，请参阅[从RemoteSynchronizedCache迁移到Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2)。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Valkey with Symfony Cache
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
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

请参阅[过时缓存选项](#stale-cache-options)，了解哪些缓存类型受益于过时缓存及其原因。

使用以下示例为`symfony_l2`过时缓存支持配置单独的前端：

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
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
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
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
| -------- | ------ | --------- | --------------------------------------------------------------------- |
| `remote_backend` | 字符串 | `'valkey'` | 远程后端类型： `valkey`或`file`。 将`valkey`用于L2缓存。 |
| `remote_backend_options` | 数组 | `[]` | 远程后端配置（请参阅Valkey文档） |
| `local_backend` | 字符串 | `'file'` | 本地后端类型： `file`或`apcu` |
| `local_backend_options` | 数组 | `[]` | 本地后端配置 |
| `cleanup_percentage` | 整数 | `95` | 一级缓存清理阈值(1-100) |
| `use_stale_cache` | 布尔型 | `false` | 启用过时缓存以实现高可用性 |
| `compress_data` | 布尔型 | `false` | 与`compression_lib`结合时启用压缩。 仅设置`compression_lib`不会启用压缩。 |
| `persistent` | 布尔型 | `true` | 控制到远程后端的持久连接。 设置为`false` (`'0'`)以匹配旧版Zend缓存行为，该行为默认为非持久连接。 |


>[!NOTE]
>
>- `remote_backend`选项也接受值`redis`，但官方不支持Redis（请参阅上文[Modern Symfony L2缓存实现](#modern-symfony-l2-cache-implementation)下的注释）。
>
>- 旧版`RemoteSynchronizedCache`配置中使用的`frontend_options.write_control`不适用于`symfony_l2`。

### 增强的Symfony L2缓存性能和可靠性

>[!NOTE]
>
>这些改进适用于使用`symfony_l2`的Adobe Commerce 2.4.9部署，并可在修补程序ACP2E-5132中找到。 对于本地Adobe Commerce，请使用Quality Patches Tool (QPT)应用此修补程序。 对于Adobe Commerce on Cloud，此修补程序通过[Commerce云修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest)自动交付。

最新的更新提高了Symfony L2缓存的可扩展性，减少了不必要的文件系统I/O，并增强了缓存一致性和可靠性。

#### 优化的Symfony L2缓存标记存储

通过消除冗余的文件系统标记索引写入，优化了Symfony L2缓存行为，以便进行Valkey支持的部署。 缓存标记现在专门存储在Valkey中，与Symfony L2缓存行为与旧版缓存实施一致。 这减少了不必要的磁盘I/O，提高了缓存写入性能，并防止了`var/cache/symfony/tags/`目录的增长。

#### 改进了基于文件的缓存行为

对于使用基于文件的缓存（没有Valkey）的部署，将继续维护本地标记索引以支持缓存失效。 标记索引现在写入配置的`cache_dir`而不是以前硬编码的`var/cache`位置，从而确保一致的缓存目录使用率并改进对自定义缓存配置的支持。

#### 重新标记后过时的标记成员身份修复

重新标记缓存条目可能会使其与不再属于它的标记相关联。 过时的标记成员身份现在会在重新标记时清除，因此缓存条目仅由当前分配给它们的标记失效。

#### 针对未更改的存储的冗余远程写修复

保存包含未更改内容的缓存条目仍会触发对远程(Valkey)后端的写入。 现在，当内容未更改时会跳过保存，从而减少不必要的远程写入。

#### 基于L1大小的逐出修复(cleanup_percentage)

用于基于L1大小的逐出的`cleanup_percentage`阈值并非始终触发清理。 L1缓存逐出现在正确遵循配置的`cleanup_percentage`。

#### 用于过时缓存的再生锁定

启用`use_stale_cache`且某个条目的远程副本暂时不可用时，现在只有一个进程会获得一个短期锁定以重新生成该条目。 对同一条目的其他并发请求将继续提供现有的局部值，而不是自己重新生成它，从而减少重新生成踩踏次数和冗余后端负载。

#### 影响

- 消除了Valkey支持的Symfony L2缓存部署中的冗余文件系统标记索引写入，减少了磁盘I/O并防止了`var/cache/symfony/tags/`目录的不必要增长。
- 确保基于文件的缓存部署始终使用为本地标记索引配置的`cache_dir`，同时保留缓存失效行为。
- 防止因重新标记后遗留的标记成员资格过时而导致的错误缓存失效。
- 减少未更改缓存保存不必要的远程写入，从而降低网络和后端负载。
- 确保在配置的`cleanup_percentage`阈值下可靠触发一级缓存逐出。
- 通过为每个键选择单个再生器而不是每个并发请求重建它，减少`use_stale_cache`条条目的再生次数。

有关详细的配置选项，请参阅：

- [使用Symfony缓存配置Valkey缓存](valkey-pg-cache.md)

>[!MORELIKETHIS]
>
>- [缓存概述和配置选项](caching-overview.md)
>- [缓存后端选项和存储引用](cache-options.md)
>- [配置缓存前端和类型](cache-types.md)
>- [为默认和页面缓存配置Redis](redis-pg-cache.md)
