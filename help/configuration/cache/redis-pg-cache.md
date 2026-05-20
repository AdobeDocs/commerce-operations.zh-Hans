---
title: 为默认缓存和页面缓存配置Redis
description: 了解如何将Redis配置为Adobe Commerce的默认和页面缓存后端。 发现CLI命令、 env.php设置和连接验证。
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: d82061ad2fa4676bd8fa71a9d34a954444eb0f54
workflow-type: tm+mt
source-wordcount: '1467'
ht-degree: 0%

---

# 为默认缓存和页面缓存配置Redis

Commerce提供了命令行选项来配置Redis页面和默认缓存。 虽然您可以通过编辑`<Commerce-install-dir>app/etc/env.php`文件来配置缓存，但建议使用命令行方法，尤其是对于初始配置。 命令行提供验证，以确保配置语法正确。

**先决条件：**

[安装Redis](config-redis.md#install-redis)，然后再继续。

>[!NOTE]
>
>对于在EC2上托管的Commerce实例，您可以使用AWS ElastiCache代替本地Redis实例。 请参阅[为EC2实例配置Elasticache](redis-elasticache-for-ec2.md)。

## 支持的框架

>[!BEGINTABS]

>[!TAB Zend缓存（2.4.8及更早版本）]

- **Zend缓存（2.4.8及更早版本）** — Commerce 2.4.8及更早版本的旧版Redis后端：
   - **旧版Redis后端** — 使用完整的类路径(`Magento\Framework\Cache\Backend\Redis`)
   - **预加载密钥** — 支持预加载常用的缓存密钥
   - **Lua脚本** — 用于垃圾回收的Lua
   - **压缩** — 支持数据压缩

>[!TAB Symfony缓存(2.4.9+)]

- **Symfony缓存(2.4.9+)** — 从Commerce 2.4.9开始，Symfony缓存为Redis提供符合PSR 6的现代化缓存实现，显着提高了性能：
   - **自动Redis流水线** — 将多个操作批处理为单个请求，减少延迟
   - **PSR-6 TagAwareAdapter** — 利用原子操作使基于标记的缓存有效失效
   - **Igbinary序列化** — 二进制序列化将缓存条目大小减少45%，速度提高5-10%
   - **增强的持久连接** — 连接池更稳定，分叉进程处理更好
   - **优化的Lua脚本** — 服务器端执行与流水线结合使用以实现最高效率

>[!ENDTABS]


## 配置Redis默认缓存

运行`setup:config:set`命令并指定Redis默认缓存的特定参数。

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

并使用以下参数：

- `--cache-backend=redis`启用Redis默认缓存。 如果已启用此功能，请忽略此参数。

- `--cache-backend-redis-<parameter>=<value>`是配置默认缓存的键值对列表：

| 命令行参数 | 值 | 含义 | 默认值 |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | 服务器 | 完全限定的主机名、IP地址或UNIX套接字的绝对路径。 默认值127.0.0.1表示Commerce服务器上安装了Redis。 | `127.0.0.1` |
| `cache-backend-redis-port` | 端口 | Redis服务器侦听端口 | `6379` |
| `cache-backend-redis-db` | 数据库 | 如果默认缓存和全页缓存都使用Redis，则此为必填字段。 指定其中一个高速缓存的数据库编号；另一个高速缓存默认使用0。<br><br>**重要提示**：如果对多种高速缓存类型使用Redis，则数据库编号必须不同。 建议将默认高速缓存数据库编号指定为0，将页高速缓存数据库编号指定为1，将会话存储数据库编号指定为2。 | `0` |
| `cache-backend-redis-password` | 密码 | 配置Redis密码可启用其内置安全功能之一： `auth`命令，该命令要求客户端进行身份验证以访问数据库。 密码直接在Redis的配置文件中配置： `/etc/redis/redis.conf` | |
| `cache-backend-redis-use-lua` | use_lua | 为所有redis操作启用或禁用Lua脚本。 <br><br>**默认值：保留在`0`。** 默认情况下，Lua模式处于禁用状态，以防止在启用Lua时捆绑的Redis库(1.17.x)出现的已知性能衰退和GraphQL缓存缺失问题。 | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | 启用或禁用垃圾回收的Lua脚本（`backend_clean_cache` cron作业）。 <br><br>**默认值：保留在`1`。** 特意启用以确保在GC期间对原子标记集进行清理。 如果没有它，当`backend_clean_cache` cron与缓存保存操作同时运行时，可能会发生争用情况，使缓存条目在缓存标记索引中没有相应的记录。 这会导致基于标记的失效静默地失败 — 例如，更新产品价格可能不会使产品缓存失效，而是需要完全缓存刷新。 | `1` |

### Lua模式

启用后，Lua模式将多个Redis操作（缓存写入、标记更新、垃圾回收）捆绑到通过`EVALSHA`在服务器端执行的单个原子脚本中。 这样可防止并发请求中的交错，例如，确保将缓存条目及其标记成员资格写入在一起。

>[!WARNING]
>
>如果不了解Adobe Commerce版本的影响，请勿更改`use_lua`和`use_lua_on_gc`的默认值：
>
>- **`use_lua`**：在Adobe Commerce 2.4.7或2.4.8（库`colinmollenhour/cache-backend-redis` 1.17.1）中启用此项可能会导致缓存损坏和GraphQL缓存丢失问题。
>- **`use_lua_on_gc`**：在Adobe Commerce 2.4.8上禁用此项将删除垃圾收集期间的原子保护，并且可能导致基于标记的缓存失效静默失败，需要完全缓存刷新才能恢复。

## 示例命令（默认缓存）

以下示例启用Redis默认缓存，将主机设置为`127.0.0.1`，并将数据库编号指定为0。 Redis对所有其他参数使用默认值。

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## 配置Redis页面缓存

要在Commerce上配置Redis页面缓存，请使用其他参数运行`setup:config:set`命令。

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

并使用以下参数：

- `--page-cache=redis`启用Redis页面缓存。 如果已启用此功能，请忽略此参数。

- `--page-cache-redis-<parameter>=<value>`是配置页面缓存的键值对列表：

| 命令行参数 | 值 | 含义 | 默认值 |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | 服务器 | 完全限定的主机名、IP地址或UNIX套接字的绝对路径。 默认值127.0.0.1表示Commerce服务器上安装了Redis。 | `127.0.0.1` |
| `page-cache-redis-port` | 端口 | Redis服务器侦听端口 | `6379` |
| `page-cache-redis-db` | 数据库 | 如果默认缓存和全页缓存都使用Redis，则此为必填字段。 指定其中一个高速缓存的数据库编号；另一个高速缓存默认使用0。<br/>**重要提示**：如果对多种高速缓存类型使用Redis，则数据库编号必须不同。 建议将默认高速缓存数据库编号指定为0，将页高速缓存数据库编号指定为1，将会话存储数据库编号指定为2。 | `0` |
| `page-cache-redis-password` | 密码 | 配置Redis密码可启用其内置安全功能之一： `auth`命令，该命令要求客户端进行身份验证以访问数据库。 在Redis配置文件中配置密码： `/etc/redis/redis.conf` | |

以下示例启用Redis页缓存，将主机设置为`127.0.0.1`，并将数据库编号分配给`1`。 所有其他参数均设置为默认值。

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### 查看Commerce环境配置

运行配置Redis缓存的命令可更新Commerce环境配置(`<Commerce-install-dir>app/etc/env.php`)：

>[!BEGINTABS]

>[!TAB Zend缓存（2.4.8及更早版本）]

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

>[!TAB Symfony缓存(2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'redis',
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
>从Commerce 2.4.9开始，使用简化的后端类型`'backend' => 'redis'`而不是完整的类路径。 当指定简化名称时，将自动使用Symfony缓存。

>[!ENDTABS]

## 配置其他缓存选项

### Redis预加载功能

由于Commerce将配置数据存储在Redis缓存中，因此您可以预加载在页面之间重复使用的数据。 要查找必须预加载的键，请分析从Redis传输到Commerce的数据。 Adobe建议预载每个页面上加载的数据，如`SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`和`DB_IS_UP_TO_DATE`。

Redis使用`pipeline`复合加载请求。 密钥应包含数据库前缀；例如，如果数据库前缀为`061_`，则预加载密钥将如下所示： `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Zend缓存]

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

>[!TAB Symfony缓存]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'redis',
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

>[!TAB Symfony缓存]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'redis',
                'backend_options' => [
                    'server' => 'redis',
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
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
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
| 缓存GET | 1-5毫秒 | 0.5-2毫秒 | 速度提高2-3倍 |
| 缓存集 | 2-6毫秒 | 0.8-2.5毫秒 | 速度提高2-3倍 |
| 标记操作 | 10-30毫秒 | 3-10毫秒 | 速度提高3至4倍 |

### 持久连接

持久连接跨请求重复使用现有Redis连接，使缓存操作速度提高5-15%。 在`app/etc/env.php`中配置：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
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
                'server' => 'redis',
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

以下是结合所有性能优化的可用于生产环境的Symfony配置：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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

## 验证Redis连接

要验证Redis和Commerce是否正确协同工作，请执行以下操作：

1. 登录到运行Redis和Commerce的服务器。
1. 打开终端。
1. 使用`redis-cli monitor`命令或`redis-cli ping`命令检查连接。

如果命令成功，则Redis正在运行，并且可以与Commerce应用程序通信。 如果失败，则Redis和Commerce之间存在一个您需要解决的连接问题。

### Redis监视命令

```shell
redis-cli monitor
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
...
```

如果两个命令都成功，则Redis设置正确。

### 检查压缩数据

要检查压缩的会话数据和页面缓存，请使用[RESP.app](https://flathub.org/apps/details/app.resp.RESP)工具。 它支持Commerce 2会话和页面缓存数据的自动解压缩，并以易于用户阅读的形式显示PHP会话数据。
