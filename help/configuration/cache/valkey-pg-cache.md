---
title: 将Valkey用于默认缓存
description: 了解如何将Valkey配置为Adobe Commerce的默认缓存。 了解命令行设置、配置选项和验证技术。
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: e9f1bef9f97a0e1d738f1221758f1b9a0a238da1
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---


# 将Valkey用于默认缓存

Commerce提供了命令行选项来配置Valkey页面和默认缓存。 虽然可以通过编辑`<Commerce-install-dir>app/etc/env.php`文件来配置缓存，但建议使用命令行来配置缓存，尤其是对于初始配置。 命令行提供验证，确保配置语法正确。

您必须[安装Valkey](config-redis.md#install-redis)，然后才能继续。

## 配置Valkey默认缓存

运行`setup:config:set`命令并指定Valkey默认缓存的参数。

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey`启用valkey默认缓存。 如果已启用此功能，请忽略此参数。

- `--cache-backend-valkey-<parameter>=<value>`是配置默认缓存的键值对列表：

>[!NOTE]
>
>从&#x200B;**Adobe Commerce 2.4.9-alpha2**&#x200B;开始，**Valkey**&#x200B;已正式替换CLI工具中的Redis，因为授权发生了更改。 Valkey是Redis的一个分支，可维护几乎相同的功能。 对于&#x200B;**版本2.4.8和更早版本**，用于配置Valkey的CLI命令与Redis的命令相同，从而确保无缝向后兼容性并简化迁移或双环境支持。 以下示例显示了特定于Valkey的命令。

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

| 命令行参数 | 值 | 含义 | 默认值 |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | 服务器 | 完全限定的主机名、IP地址或UNIX套接字的绝对路径。 默认值`127.0.0.1`表示Commerce服务器上安装了Valkey。 | `127.0.0.1` |
| `cache-backend-valkey-port` | 端口 | Valkey服务器侦听端口 | `6379` |
| `cache-backend-valkey-db` | 数据库 | 如果对默认缓存和全页缓存都使用Valkey，则此为必填字段。 必须指定其中一个缓存的数据库编号；默认情况下，另一个缓存使用`0`。<br><br>**重要信息**：如果对多种类型的缓存使用Valkey，则数据库编号必须不同。 Adobe建议将默认缓存数据库编号分配给`0`，将页面缓存数据库编号分配给`1`，将会话存储数据库编号分配给`2`。 | `0` |
| `cache-backend-valkey-password` | 密码 | 配置Valkey密码可启用其内置安全功能之一： `auth`命令，该命令要求客户端进行身份验证以访问数据库。 密码直接在Valkey配置文件中配置： `/etc/valkey/valkey.conf` | |

### 示例命令

以下示例启用Valkey默认缓存，将主机设置为`127.0.0.1`，并将数据库编号分配给`0`。 Valkey对所有其他参数使用默认值。

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

>[!NOTE]
>
>从&#x200B;**Adobe Commerce 2.4.9-alpha2**&#x200B;开始，**Valkey**&#x200B;已正式替换CLI工具中的Redis，因为授权发生了更改。 Valkey是Redis的一个分支，可维护几乎相同的功能。 对于&#x200B;**版本2.4.8和更早版本**，用于配置Valkey的CLI命令与Redis的命令相同，从而确保无缝向后兼容性并简化迁移或双环境支持。 以下示例显示了特定于Valkey的命令。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## 配置页面缓存

要在Commerce上配置Valkey页缓存，请使用其他参数运行`setup:config:set`命令。

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

并使用以下参数：

- `--page-cache=valkey`启用Valkey页缓存。 如果已启用此功能，请忽略此参数。

- `--page-cache-valkey-<parameter>=<value>`是配置页面缓存的键值对列表：

>[!NOTE]
>
>从&#x200B;**Adobe Commerce 2.4.9-alpha2**&#x200B;开始，**Valkey**&#x200B;已正式替换CLI工具中的Redis，因为授权发生了更改。 Valkey是Redis的一个分支，可维护几乎相同的功能。 对于&#x200B;**版本2.4.8和更早版本**，用于配置Valkey的CLI命令与Redis的命令相同，从而确保无缝向后兼容性并简化迁移或双环境支持。 以下示例显示了特定于Valkey的命令。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

| 命令行参数 | 值 | 含义 | 默认值 |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | 服务器 | 完全限定的主机名、IP地址或UNIX套接字的绝对路径。 默认值`127.0.0.1`表示Commerce服务器上安装了Valkey。 | `127.0.0.1` |
| `page-cache-valkey-port` | 端口 | Valkey服务器侦听端口。 | `6379` |
| `page-cache-valkey-db` | 数据库 | 如果您对默认缓存和全页缓存都使用Valkey，则此为必填字段。 必须指定其中一个缓存的数据库编号；默认情况下，另一个缓存使用`0`。<br/>**重要信息**：如果对多种类型的缓存使用Valkey，则数据库编号必须不同。 建议将默认缓存数据库编号分配给`0`，将页面缓存数据库编号分配给`1`，将会话存储数据库编号分配给`2`。 | `0` |
| `page-cache-valkey-password` | 密码 | 配置Valkey密码可启用其内置安全功能之一： `auth`命令，该命令要求客户端进行身份验证以访问数据库。 在Valkey配置文件中配置密码： `/etc/valkey/valkey.conf` | |

### 示例命令

以下示例启用Valkey页缓存，将主机设置为`127.0.0.1`，并将数据库编号分配给`1`。 所有其他参数均设置为默认值。

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

>[!NOTE]
>
>从&#x200B;**Adobe Commerce 2.4.9-alpha2**&#x200B;开始，**Valkey**&#x200B;已正式替换CLI工具中的Redis，因为授权发生了更改。 Valkey是Redis的一个分支，可维护几乎相同的功能。 对于&#x200B;**版本2.4.8和更早版本**，用于配置Valkey的CLI命令与Redis的命令相同，从而确保无缝向后兼容性并简化迁移或双环境支持。 以下示例显示了特定于Valkey的命令。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-valkey-db=1
```

## 结果

作为两个示例命令的结果，Commerce在`<Commerce-install-dir>app/etc/env.php`中添加了类似于以下内容的行：

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

## 新的Valkey缓存实施

[!BADGE 2.4.9-alpha]{type=Negative tooltip="仅在2.4.9 alpha版中提供。"}

从Adobe Commerce 2.4.9开始，Adobe建议使用Valkey缓存实现： `\Magento\Framework\Cache\Backend\Valkey`。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Valkey预加载功能

由于Commerce将配置数据存储在Valkey缓存中，因此您可以预加载在页面之间重复使用的数据。 要查找必须预加载的键，请分析从Valkey传输到Commerce的数据。 Adobe建议预载每个页面上加载的数据，如`SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`和`DB_IS_UP_TO_DATE`。

Valkey使用`pipeline`复合加载请求。 密钥应包含数据库前缀；例如，如果数据库前缀为`061_`，则预加载密钥将如下所示： `061_SYSTEM_DEFAULT`

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

将预加载功能与L2缓存结合使用时，必须将`:hash`后缀添加到您的密钥中。 L2缓存只传输数据的散列，而不传输实际数据。

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## 并行生成

从Commerce 2.4.0版本开始，Adobe为想要消除等待锁定的用户引入了`allow_parallel_generation`选项。
默认情况下，该选项处于禁用状态，Adobe建议禁用该选项，直到您拥有过多的配置和/或块。

**要启用并行生成**：

```bash
bin/magento setup:config:set --allow-parallel-generation
```

由于它是一个标志，因此不能用命令禁用它。 您必须手动将配置值设置为`false`：

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'redis',
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

## 验证Valkey连接

要验证Valkey和Commerce是否正常工作，请登录到运行Valkey的服务器，打开终端，然后使用`valkey-cli monitor`命令或`redis-cli ping`命令。

### Valkey monitor命令

```bash
valkey-cli monitor
```

页面缓存输出示例：

```
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

```bash
valkey-cli ping
```

预期的响应为： `PONG`

如果两个命令都成功，则Valkey设置正确。

### 检查压缩数据

为了检查压缩的会话数据和页面缓存，[RESP.app](https://flathub.org/apps/app.resp.RESP)支持Commerce 2会话和页面缓存的自动解压缩，并以人类可读的格式显示PHP会话数据。
