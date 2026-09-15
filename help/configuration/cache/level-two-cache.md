---
title: 用于性能优化的二级缓存配置
description: 了解如何在Adobe Commerce内部部署中配置二级缓存以减少网络流量并提高性能。 将旧版RemoteSynchronizedCache实施与新版Symfony L2实施进行比较。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hans/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce内部部署项目。"
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: ea07c4a7e42988b2ede3511273261fa7d560b652
workflow-type: tm+mt
source-wordcount: '1686'
ht-degree: 0%
---
# 用于性能优化的二级缓存配置

L2（两级）缓存通过在每个Web节点上添加本地缓存层，减少了远程缓存服务与Commerce应用程序之间的网络流量。 每个请求一个标准Commerce实例可以传输大约300 KB。 在高请求量下，产生的网络流量可能会相当大。

通过二级缓存，每个Web节点将经常访问的数据存储在本地，并将远程缓存用于两个目的：

- 检查缓存数据版本，确保最新的缓存存储在本地
- 正在将更新的缓存数据从远程缓存服务传输到本地计算机

Commerce会将经过哈希处理的数据版本存储在远程缓存中，并将后缀`:hash`附加到常规键中。 当本地缓存过期时，将通过缓存适配器从远程缓存服务中获取数据。

可用的二级缓存实施取决于Commerce版本和修补程序级别：

| 实现 | Commerce版本 | 远程缓存服务 | 描述 |
| -------------- | ---------------- | -------------------- | ----------- |
| [`RemoteSynchronizedCache`](#remotesynchronizedcache-l2-cache-configuration) | 在2.4.9之前，如果支持 | Redis或Valkey，具体取决于版本和修补程序级别 | 基于Zend的二级缓存，具有`Cm_Cache_Backend_File`用于本地存储 |
| [Symfony L2 (`symfony_l2`)](#symfony-l2-cache-implementation) | 2.4.9及更高版本 | Valkey | 符合PSR-6要求的现代Symfony基于缓存的L2实施 |

## RemoteSynchronizedCache二级缓存配置


>[!NOTE]
>
>本节介绍低于2.4.9的Adobe Commerce本地版本的`RemoteSynchronizedCache` L2配置，这些版本受确切的Commerce发行版和修补程序级别支持列表支持。
>
>对于Adobe Commerce 2.4.9及更高版本，请将Valkey与[Symfony L2缓存](#symfony-l2-cache-implementation)一起使用。
>
>对于云基础架构上的Adobe Commerce，请通过`.magento.env.yaml`中的部署变量配置二级缓存。 不要直接编辑`app/etc/env.php`。 请参阅[配置二级缓存](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache)。

缓存配置说明取决于您的Commerce版本：

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
  - `remote_backend`是远程缓存实现： Redis或Valkey，具体取决于Commerce版本和修补程序级别的支持。
  - `remote_backend_options`是远程缓存配置。
  - `local_backend`是本地缓存实现： `Cm_Cache_Backend_File`。
  - `local_backend_options`是本地缓存配置。
  - `cache_dir`是文件缓存特定的选项，它定义存储本地缓存的目录。

对于早于2.4.9且支持Redis或Valkey的Adobe Commerce版本，Adobe建议使用Redis或Valkey进行远程缓存，如确切版本所支持，并使用`Cm_Cache_Backend_File`进行本地缓存。 本地缓存通常存储在临时文件系统上，如`/dev/shm/`：

```php
'local_backend_options' => [
    'cache_dir' => '/dev/shm/'
]
```

Adobe建议使用`[cache preload](redis-pg-cache.md#redis-preload-feature)`功能，因为它减少了Redis上的负载。 请确保为预加载密钥添加后缀`:hash`。

## 过时的缓存选项

从Commerce 2.4开始，`use_stale_cache`选项通过在并行进程中生成新缓存数据时提供以前缓存的数据，可以在特定情况下提高性能。 本节中介绍的建议缓存类型和权衡适用于`RemoteSynchronizedCache`和`symfony_l2`实施。 有关`symfony_l2`配置示例，请参阅[Symfony L2缓存和过时的缓存](#symfony-l2-cache-with-stale-cache)。

通常，从性能角度来看，锁定等待的权衡是可以接受的。 但是，随着块数或缓存条目的增加，锁定需要更多时间。 在某些情况下，等待时间最多可以为进程的&#x200B;**键数** x **查找超时**。 在极少数情况下，一个用户在`Block/Config`缓存中可能有数百个密钥，因此，即使是较小的锁查找超时也可能需要几秒钟。

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

以下代码显示了`RemoteSynchronizedCache`后端的示例配置。 有关`symfony_l2`示例，请参阅[Symfony L2缓存和过时的缓存](#symfony-l2-cache-with-stale-cache)。

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

## Symfony L2缓存实施

在Commerce版本2.4.9+中，使用Symfony L2缓存实现（`symfony_l2`后端）而不是`RemoteSynchronizedCache`。 Symfony L2缓存使用Valkey提供了与PSR 6兼容的缓存实施。

>[!IMPORTANT]
>
>以下Adobe Commerce版本中的缓存配置不支持Redis：
>
>- Adobe Commerce 2.4.9及更高版本
>- Adobe Commerce 2.4.8-p4及更高版本的修补程序
>- Adobe Commerce 2.4.7-p9及更高版本的修补程序
>- Adobe Commerce 2.4.6-p14及更高版本的修补程序
>- Adobe Commerce 2.4.5-p16及更高版本的修补程序
>
>对于这些版本，请配置Valkey。
>
>如果在Adobe Commerce 2.4.9或更高版本上为L2缓存配置`symfony_l2`，则必须将Valkey用于远程缓存服务。 请参阅[设置Valkey](config-valkey.md)。

### 从RemoteSynchronizedCache迁移到Symfony L2

如果您要将内部部署安装从`RemoteSynchronizedCache`后端升级到`symfony_l2`，请在更新`app/etc/env.php`之前查看以下内容。 仅更改`backend`值是不够的。 配置结构、键名和某些默认行为各不相同。

- **配置结构已更改。** `remote_backend`、`remote_backend_options`和`local_backend`在`symfony_l2`下使用不同的值。 例如，`remote_backend`变为`'valkey'`而不是完全限定的类名。 使用下面的[配置示例](#configuration-example-with-symfony-l2-cache)作为您的起点，而不是就地编辑您现有的`RemoteSynchronizedCache`配置。

- 不建议将&#x200B;**`preload_keys`与`symfony_l2`.**&#x200B;一起使用 如果`RemoteSynchronizedCache`配置包含`preload_keys`，请在迁移过程中将其删除。 预加载密钥不会提高`symfony_l2`下的性能，并且会触发其他不必要的密钥查找，从而增加Valkey的负载。

- **压缩需要一个显式标志。** 仅设置`compression_lib`不会在`symfony_l2`下启用压缩。 有关所需的`compress_data`设置，请参阅Symfony L2缓存的[后端选项](#backend-options-for-symfony-l2-cache)。

- **手动配置的内部部署默认情况下不启用过时的缓存。** `symfony_l2`下的`use_stale_cache`默认为`false`（请参阅[后端选项表](#backend-options-for-symfony-l2-cache)）。 如果您的`RemoteSynchronizedCache`配置使用了`stale_cache_enabled`前端，则必须使用[Symfony L2缓存中的模式显式重新创建该前端，该模式具有过时的缓存](#symfony-l2-cache-with-stale-cache)。

>[!NOTE]
>
>设置`VALKEY_BACKEND: symfony_l2`部署变量的云环境上的Adobe Commerce具有由`ece-tools`自动生成的完整L2配置，包括`stale_cache_enabled`前端。 请参阅[配置Symfony L2缓存](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)以了解特定于云的行为。

- **Redis不是`symfony_l2`支持的远程后端。** 作为此更改的一部分，请迁移到Valkey。 请参阅[设置Valkey](config-valkey.md)。

### Symfony L2缓存的配置示例

>[!IMPORTANT]
>
>此`app/etc/env.php`示例仅适用于内部部署。 对于云基础架构上的Adobe Commerce，请勿直接编辑`app/etc/env.php`。 在`.magento.env.yaml`中设置`VALKEY_BACKEND: symfony_l2`。 `ece-tools`在部署期间生成并维护二级缓存配置。 请参阅[配置Symfony L2缓存](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)。

在`app/etc/env.php`文件中，为L2缓存使用简化的`symfony_l2`后端类型。 此示例不包括`preload_keys`配置，不建议对`symfony_l2`使用此配置。 有关详细信息，请参阅[从RemoteSynchronizedCache迁移到Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2)。

该示例将`cleanup_percentage`设置为`90`。 默认值为`95`。 根据可用的本地缓存存储和Commerce部署要求调整此值。

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
| -------- | ------ | --------- | ----------- |
| `remote_backend` | 字符串 | `'valkey'` | 远程缓存后端。 将`valkey`与Symfony L2一起使用。 官方不支持Redis。 |
| `remote_backend_options` | 数组 | `[]` | 远程Valkey后端配置 |
| `local_backend` | 字符串 | `'file'` | 本地后端类型： `file`或`apcu` |
| `local_backend_options` | 数组 | `[]` | 本地后端配置 |
| `cleanup_percentage` | 整数 | `95` | 一级缓存清理阈值，以1到100之间的百分比表示 |
| `use_stale_cache` | 布尔型 | `false` | 为前端启用过时缓存 |
| `compress_data` | 布尔型 | `false` | 与`compression_lib`结合时启用压缩。 在远程Valkey后端选项中设置此选项。 |
| `persistent` | 布尔型 | `true` | 控制到远程后端的持久连接。 设置为`false` (`'0'`)以匹配Zend缓存行为，该行为默认为非持久连接。 |

>[!NOTE]
>
>`frontend_options.write_control`选项适用于`RemoteSynchronizedCache`配置，而不适用于`symfony_l2`。

### 增强的Symfony L2缓存性能和可靠性

>[!NOTE]
>
>这些改进适用于使用`symfony_l2`的Adobe Commerce 2.4.9部署，并可在修补程序ACP2E-5132中找到。
>
>对于本地Adobe Commerce，请使用Quality Patches Tool (QPT)应用此修补程序。 对于Adobe Commerce on Cloud Infrastructure，该修补程序包含在Commerce的云修补程序包中，它依赖于`ece-tools`。 更新到`ece-tools`的最新版本以在部署期间接收最新的Cloud修补程序。

最新的更新提高了Symfony L2缓存的可扩展性，减少了不必要的文件系统I/O，并增强了缓存一致性和可靠性。

#### 优化的Symfony L2缓存标记存储

对于Valkey支持的Symfony L2缓存部署，缓存标记仅存储在Valkey中。 这消除了冗余的文件系统标记索引写入，减少了磁盘I/O，并防止了`var/cache/symfony/tags/`目录的不必要增长。

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
- 通过为每个键选择单个再生器而不是让每个并发请求重新生成条目，减少`use_stale_cache`条目的再生次数。

有关详细的配置选项，请参阅：

- [使用Symfony缓存配置Valkey缓存](valkey-pg-cache.md)
