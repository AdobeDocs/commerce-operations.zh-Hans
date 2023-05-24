---
title: 将Redis用于默认缓存
description: 了解如何将Redis配置为Adobe Commerce和Magento Open Source的默认缓存。
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# 将Redis用于默认缓存

Commerce提供命令行选项来配置Redis页面和默认缓存。 虽然您可以通过编辑 `<Commerce-install-dir>app/etc/env.php` 文件，使用命令行是推荐的方法，尤其是对于初始配置。 命令行提供验证，确保配置语法正确。

您必须 [安装Redis](config-redis.md#install-redis) 然后再继续。

## 配置Redis默认缓存

运行 `setup:config:set` 命令并指定特定于Redis默认缓存的参数。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

，并使用以下参数：

- `--cache-backend=redis` 启用Redis默认缓存。 如果已启用此功能，请忽略此参数。

- `--cache-backend-redis-<parameter>=<value>` 是配置默认缓存的键值对列表：

| 命令行参数 | 值 | 含义 | 默认值 |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | 服务器 | UNIX套接字的完全限定主机名、IP地址或绝对路径。 默认值127.0.0.1表示Commerce服务器上安装了Redis。 | `127.0.0.1` |
| `cache-backend-redis-port` | 端口 | Redis服务器侦听端口 | `6379` |
| `cache-backend-redis-db` | 数据库 | 如果您同时将Redis用于默认缓存和全页缓存，则此为必填字段。 必须指定其中一个高速缓存的数据库编号；缺省情况下另一个高速缓存使用0。<br><br>**重要**：如果将Redis用于多种类型的缓存，则数据库编号必须不同。 建议将默认高速缓存数据库编号指定为0，将页高速缓存数据库编号指定为1，将会话存储数据库编号指定为2。 | `0` |
| `cache-backend-redis-password` | 密码 | 配置Redis密码可启用其内置安全功能之一： `auth` 命令，它要求客户端进行身份验证以访问数据库。 密码直接在Redis的配置文件中配置： `/etc/redis/redis.conf` |  |

### 示例命令

以下示例启用Redis默认缓存，并将主机设置为 `127.0.0.1`，并将数据库编号分配给0。 Redis对所有其他参数使用默认值。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## 配置Redis页面缓存

要在Commerce上配置Redis页面缓存，请运行 `setup:config:set` 命令。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

，并使用以下参数：

- `--page-cache=redis` 启用Redis页面缓存。 如果已启用此功能，请忽略此参数。

- `--page-cache-redis-<parameter>=<value>` 是用于配置页面缓存的键值对列表：

| 命令行参数 | 值 | 含义 | 默认值 |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | 服务器 | UNIX套接字的完全限定主机名、IP地址或绝对路径。 默认值127.0.0.1表示Commerce服务器上安装了Redis。 | `127.0.0.1` |
| `page-cache-redis-port` | 端口 | Redis服务器侦听端口 | `6379` |
| `page-cache-redis-db` | 数据库 | 如果您同时将Redis用于默认缓存和全页缓存，则此为必填字段。 必须指定其中一个高速缓存的数据库编号；缺省情况下另一个高速缓存使用0。<br/>**重要**：如果将Redis用于多种类型的缓存，则数据库编号必须不同。 建议将默认高速缓存数据库编号指定为0，将页高速缓存数据库编号指定为1，将会话存储数据库编号指定为2。 | `0` |
| `page-cache-redis-password` | 密码 | 配置Redis密码可启用其内置安全功能之一： `auth` 命令，它要求客户端进行身份验证以访问数据库。 在Redis配置文件中配置密码： `/etc/redis/redis.conf` |  |

### 示例命令

以下示例启用Redis页面缓存，并将主机设置为 `127.0.0.1`，并将数据库编号分配给1。 所有其他参数均设置为默认值。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## 结果

作为两个示例命令的结果，Commerce将类似于以下内容的行添加到 `<Commerce-install-dir>app/etc/env.php`：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
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

## 在EC2实例中使用AWS ElastiCache

从Commerce 2.4.3开始，在Amazon EC2上托管的实例可以使用AWS ElastiCache代替本地Redis实例。

>[!WARNING]
>
>本节仅适用于在Amazon EC2 VPC上运行的Commerce实例。 它不适用于内部部署。

### 配置Redis群集

晚于 [在AWS上设置Redis聚类](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/)，配置EC2实例以使用ElastiCache。

1. [创建ElastiCache集群](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) EC2实例的同一区域和VPC中。
1. 验证连接。

   - 打开到EC2实例的SSH连接
   - 在EC2实例上，安装Redis客户端：

      ```bash
      sudo apt-get install redis
      ```

   - 将入站规则添加到EC2安全组：类型 `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 将入站规则添加到ElastiCache群集安全组：类型 `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - 连接到Redis CLI：

      ```bash
      redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
      ```

### 配置Commerce以使用聚类

Commerce支持多种类型的缓存配置。 通常，缓存配置在前端和后端之间拆分。 前端缓存被分类为 `default`，用于任何缓存类型。 您可以自定义或拆分为较低级别的缓存以实现更好的性能。 一种常见的Redis配置是将默认缓存和页面缓存分隔到各自的Redis数据库(RDB)中。

运行 `setup` 用于指定Redis端点的命令。

要将Commerce for Redis配置为默认缓存，请执行以下操作：

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

要为Redis页面缓存配置Commerce：

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

要将Commerce配置为使用Redis进行会话存储，请执行以下操作：

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 验证连通性

**验证Commerce是否正在与ElastiCache通信**：

1. 打开到Commerce EC2实例的SSH连接。
1. 启动Redis监视器。

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. 在Commerce UI中打开页面。
1. 验证 [缓存输出](#verify-redis-connection) 在你的终端机里。

## 新的Redis缓存实施

从Commerce 2.3.5开始，建议使用扩展的Redis缓存实施： `\Magento\Framework\Cache\Backend\Redis`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Redis预加载功能

由于Commerce将配置数据存储在Redis缓存中，因此我们可以预加载在页面之间重复使用的数据。 要查找必须预加载的键，请分析从Redis传输到Commerce的数据。 我们建议预先加载在每个页面上加载的数据，例如 `SYSTEM_DEFAULT`， `EAV_ENTITY_TYPES`， `DB_IS_UP_TO_DATE`.

Redis使用 `pipeline` 以便复合加载请求。 键应包含数据库前缀；例如，如果数据库前缀为 `061_`，预加载键如下所示： `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
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

如果您要将预加载功能与L2缓存一起使用，请不要忘记添加 `:hash` 后缀到您的密钥中，因为L2缓存仅传输数据的哈希，而不传输数据本身：

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## 并行生成

从2.4.0版本开始，我们引入了 `allow_parallel_generation` 用户希望取消等待锁的选项。
默认情况下，该选项处于禁用状态，我们建议禁用该选项，直到您拥有过多的配置和/或块。

**启用并行生成**：

```bash
bin/magento setup:config:set --allow-parallel-generation
```

由于它是一个标志，因此不能使用命令禁用它。 您必须手动将配置值设置为 `false`：

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
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

## 验证Redis连接

要验证Redis和Commerce是否协同工作，请登录到运行Redis的服务器，打开终端，然后使用Redis monitor命令或ping命令。

### Redis监视器命令

```bash
redis-cli monitor
```

页面缓存输出示例：

```terminal
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

### Redis ping命令

```bash
redis-cli ping
```

预期响应为： `PONG`

如果两个命令都成功，则Redis设置正确。

### 检查压缩数据

要检查压缩的会话数据和页面缓存，请 [RESP.app](https://flathub.org/apps/details/app.resp.RESP) 支持Commerce 2会话和页面缓存的自动解压缩，并以易于用户阅读的形式显示PHP会话数据。
