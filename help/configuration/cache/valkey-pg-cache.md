---
title: 为默认缓存和页面缓存配置Valkey
description: 了解如何将Valkey配置为Adobe Commerce的默认和页面缓存后端。 发现CLI命令、 env.php设置和连接验证。
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
autotag-review: '2026-06-22T22:00:55.389Z'
TQID: 'https://experienceleague.adobe.com/AjJ86dYGRVFuY1T73ct1Gpcf6iDbb4ewP8OiGX8otQs'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 1281
ht-degree: 0%

---


# 为默认缓存和页面缓存配置Valkey

Commerce提供了命令行选项来配置Valkey默认值和页面缓存。 虽然可以通过编辑`<Commerce-install-dir>app/etc/env.php`文件来配置缓存，但建议使用命令行来配置缓存，尤其是对于初始配置。 命令行提供验证，确保配置语法正确。

{{cloud-cache-config}}

**先决条件：**

[先安装Valkey](config-valkey.md#install-valkey)，然后再继续。

## 支持的框架

>[!BEGINTABS]

>[!TAB Zend缓存（2.4.8及更早版本）]

- **Zend缓存（2.4.8及更早版本）** — Commerce 2.4.8及更早版本的旧版Valkey后端：
   - **旧版Valkey后端** — 使用完整的类路径(`Magento\Framework\Cache\Backend\Valkey`)
   - **预加载密钥** — 支持预加载常用的缓存密钥
   - **Lua脚本** — 用于垃圾回收的Lua
   - **压缩** — 支持数据压缩

>[!TAB Symfony缓存(2.4.9+)]

- **Symfony缓存(2.4.9+)** — 从Commerce 2.4.9开始，Symfony缓存为Valkey提供了一个符合PSR 6的现代化缓存实现，并显着提高了性能：
   - **自动Valkey流水线** — 将多个操作批处理为单个请求，减少延迟
   - **PSR-6 TagAwareAdapter** — 利用原子操作使基于标记的缓存有效失效
   - **Igbinary序列化** — 二进制序列化将缓存条目大小减少45%，速度提高5-10%
   - **增强的持久连接** — 连接池更稳定，分叉进程处理更好
   - **优化的Lua脚本** — 服务器端执行与流水线结合使用以实现最高效率

>[!ENDTABS]

## 配置Valkey默认缓存

运行`setup:config:set`命令并指定Valkey默认缓存的参数。

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey`启用Valkey默认缓存。 如果已启用此功能，请忽略此参数。

- `--cache-backend-valkey-<parameter>=<value>`是配置默认缓存的键值对列表：

{{valkey-redis-cli-note}}

| 命令行参数 | 值 | 含义 | 默认值 |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | 服务器 | 完全限定的主机名、IP地址或UNIX套接字的绝对路径。 默认值`127.0.0.1`表示Commerce服务器上安装了Valkey。 | `127.0.0.1` |
| `cache-backend-valkey-port` | 端口 | Valkey服务器侦听端口 | `6379` |
| `cache-backend-valkey-db` | 数据库 | 如果对默认缓存和全页缓存都使用Valkey，则此为必填字段。 指定其中一个缓存的数据库编号；另一个缓存默认使用`0`。<br><br>**重要信息**：如果对多种类型的缓存使用Valkey，则数据库编号必须不同。 Adobe建议将默认缓存数据库编号分配给`0`，将页面缓存数据库编号分配给`1`，将会话存储数据库编号分配给`2`。 | `0` |
| `cache-backend-valkey-password` | 密码 | 配置Valkey密码可启用其内置安全功能之一： `auth`命令，该命令要求客户端进行身份验证以访问数据库。 密码直接在Valkey的配置文件中配置： `/etc/valkey/valkey.conf` | |
| `cache-backend-valkey-use-lua` | use_lua | 启用或禁用LUA。 <br><br>**LUA**： Lua使我们能够在Valkey中运行部分应用程序逻辑，从而改善性能并通过其原子执行确保数据一致性。 | `0` |
| `cache-backend-valkey-use-lua-on-gc` | use_lua_on_gc | 为垃圾收集启用或禁用LUA。 <br><br>**LUA**： Lua使我们能够在Valkey中运行部分应用程序逻辑，从而改善性能并通过其原子执行确保数据一致性。 | `1` |

## 示例命令（默认缓存）

以下示例启用Valkey默认缓存，将主机设置为`127.0.0.1`，并将数据库编号分配给`0`。 Valkey对所有其他参数使用默认值。

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

{{valkey-redis-cli-note}}

## 配置Valkey页面缓存

要在Commerce上配置Valkey页缓存，请使用其他参数运行`setup:config:set`命令。

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

并使用以下参数：

- `--page-cache=valkey`启用Valkey页缓存。 如果已启用此功能，请忽略此参数。

- `--page-cache-valkey-<parameter>=<value>`是配置页面缓存的键值对列表：

| 命令行参数 | 值 | 含义 | 默认值 |
|----------------------------------------| --------- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | 服务器 | 完全限定的主机名、IP地址或UNIX套接字的绝对路径。 默认值`127.0.0.1`表示Commerce服务器上安装了Valkey。 | `127.0.0.1` |
| `page-cache-valkey-port` | 端口 | Valkey服务器侦听端口。 | `6379` |
| `page-cache-valkey-db` | 数据库 | 如果您对默认缓存和全页缓存都使用Valkey，则此为必填字段。 指定其中一个缓存的数据库编号；另一个缓存默认使用`0`。<br/>**重要信息**：如果对多种类型的缓存使用Valkey，则数据库编号必须不同。 建议将默认缓存数据库编号分配给`0`，将页面缓存数据库编号分配给`1`，将会话存储数据库编号分配给`2`。 | `0` |
| `page-cache-valkey-password` | 密码 | 配置Valkey密码可启用其内置安全功能之一： `auth`命令，该命令要求客户端进行身份验证以访问数据库。 在Valkey配置文件中配置密码： `/etc/valkey/valkey.conf` | |

### 示例命令(page cache)

以下示例启用Valkey页缓存，将主机设置为`127.0.0.1`，并将数据库编号分配给`1`。 所有其他参数均设置为默认值。

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

{{valkey-redis-cli-note}}

### 查看Commerce环境配置

运行配置Valkey缓存的命令将更新Commerce环境配置(`<Commerce-install-dir>app/etc/env.php`)：

>[!BEGINTABS]

>[!TAB Zend缓存（2.4.8及更早版本）]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

>[!TAB Symfony缓存(2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

>[!NOTE]
>
>从Commerce 2.4.9开始，使用简化的后端类型`'backend' => 'valkey'`而不是完整的类路径。 当指定简化名称时，将自动使用Symfony缓存。

>[!ENDTABS]

## 配置其他缓存选项

### Valkey预加载功能

由于Commerce将配置数据存储在Valkey缓存中，因此您可以预加载在页面之间重复使用的数据。 要查找必须预加载的键，请分析从Valkey传输到Commerce的数据。 Adobe建议预载每个页面上加载的数据，如`SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`和`DB_IS_UP_TO_DATE`。

Valkey使用`pipeline`复合加载请求。 密钥应包含数据库前缀；例如，如果数据库前缀为`061_`，则预加载密钥将如下所示： `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Zend缓存]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

>[!TAB Symfony缓存]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

>[!ENDTABS]

将预加载功能与L2缓存结合使用时，必须将`:hash`后缀添加到您的密钥中。 L2缓存只传输数据的散列，而不传输实际数据。

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### 并行生成

从Commerce 2.4.0版本开始，Adobe为希望消除等待锁定的用户引入了`allow_parallel_generation`选项。 默认情况下，该选项处于禁用状态，Adobe建议禁用该选项，直到您拥有过多的配置和/或块。

**要启用并行生成**：

```shell
bin/magento setup:config:set --allow-parallel-generation
```

由于它是一个标志，因此不能用命令禁用它。 手动将配置值设置为`false`：

>[!BEGINTABS]

>[!TAB Zend缓存]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'valkey',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!TAB Symfony缓存]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'valkey',
                'backend_options' => [
                    'server' => 'valkey',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compress_data' => '1',
                    'compression_lib' => 'gzip'
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!ENDTABS]

## Symfony缓存性能优化

如果使用Symfony缓存，则可以通过配置Igbinary序列化程序、安装igbinary PHP扩展和phpredis扩展以及启用永久连接来进一步优化性能。

### Igbinary序列化程序

与PHP的默认序列化相比，Igbinary序列化程序提供了显着的性能改进。 必须在`app/etc/env.php`中手动配置它：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### 安装PHP Igbinary扩展

要使用igbinary序列化，必须安装PHP Igbinary扩展。

**使用apt（建议用于Debian/Ubuntu）**：

```bash
sudo apt-get install php-igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

**使用pecl（替代方法）**：

```bash
sudo pecl install igbinary
echo "extension=igbinary.so" | sudo tee /etc/php/8.3/mods-available/igbinary.ini
sudo phpenmod igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

### PHP Redis扩展：phpredis与Predis

Commerce 2.4.9+包括在phpredis（原生C扩展）和Predis（纯PHP库）之间的自动回退。 为获得最佳性能，请安装phpredis ：

**使用apt（建议用于Debian/Ubuntu）**：

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**使用pecl（替代方法）**：

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/8.3/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**性能比较**：

| 操作 | Predis | phpredis | 改进 |
|-----------|--------|----------|-------------|
| 缓存获取 | 1-5毫秒 | 0.5-2毫秒 | 速度提高2-3倍 |
| 缓存集 | 2-6毫秒 | 0.8-2.5毫秒 | 速度提高2-3倍 |
| 标记操作 | 10-30毫秒 | 3-10毫秒 | 速度提高3至4倍 |

### 持久连接

持久连接跨请求重用现有的Valkey连接，使缓存操作速度提高5-15%。 在`app/etc/env.php`中配置：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ]
]
```

>[!IMPORTANT]
>
>为每种缓存类型使用唯一的`persistent_id`以防止连接冲突。

### 完成优化的配置

以下是结合所有性能优化的适用于生产的配置：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '1',
                'compression_lib' => 'gzip',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
                'use_lua' => '1',
                'use_lua_on_gc' => '1',
                'preload_keys' => [
                    'b0b_EAV_ENTITY_TYPES',
                    'b0b_GLOBAL_PLUGIN_LIST',
                    'b0b_DB_IS_UP_TO_DATE',
                    'b0b_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '0',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ],
    'allow_parallel_generation' => false
]
```

## 验证Valkey连接

要验证Valkey和Commerce是否正确协同工作，请执行以下操作：

1. 登录到运行Valkey和Commerce的服务器。
1. 打开终端。
1. 使用`valkey-cli monitor`命令或`valkey-cli ping`命令检查连接。

如果命令成功，则Valkey正在运行，并且可以与Commerce应用程序通信。 如果失败，则Valkey和Commerce之间存在一个您需要解决的连接问题。

### Valkey monitor命令

```shell
valkey-cli monitor
```

页面缓存输出示例：

```text
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Valkey ping命令

```shell
valkey-cli ping
```

预期的响应为： `PONG`

如果两个命令都成功，则Valkey设置正确。

### 检查压缩数据

要检查压缩的会话数据和页面缓存，请使用[RESP.app](https://flathub.org/apps/app.resp.RESP)工具。 它支持Commerce 2会话和页面缓存数据的自动解压缩，并以易于用户阅读的格式显示PHP会话数据。

