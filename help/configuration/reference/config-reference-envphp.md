---
title: env.php引用
description: 请参阅env.php文件的值列表。
source-git-commit: fe5e16d44213d1864a62230029e9e206eecd1717
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---


# env.php引用

的 `env.php` 文件包含以下部分：

| 名称 | 描述 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | “管理员”区域的设置 |
| `cache` | 配置密文页面和默认缓存 |
| `cache_types` | 缓存存储设置 |
| `consumers_wait_for_messages` | 配置用户处理来自消息队列的消息的方式 |
| `cron` | 启用或禁用cron作业 |
| `crypt` | 加密函数的加密密钥 |
| `db` | 数据库连接设置 |
| `default_connection` | 消息队列默认连接 |
| `directories` | 商务目录映射设置 |
| `downloadable_domains` | 可下载域列表 |
| `install` | 安装日期 |
| `lock` | 锁定提供程序设置 |
| `MAGE_MODE` | 的 [应用程序模式](../bootstrap/application-modes.md) |
| `queue` | [消息队列](../queues/manage-message-queues.md) 设置 |
| `resource` | 将资源名称映射到连接 |
| `session` | 会话存储数据 |
| `system` | 禁用在管理员中编辑的字段 |
| `x-frame-options` | 设置 [x-frame-options][x-frame-options] |

## 后端

配置 **frontName** 对于商务管理员url，使用 `backend` env.php中的节点。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## 缓存

使用配置Redis页面和默认缓存 `cache` 节点 `env.php` 文件。

```conf
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
]
```

在 [Redis配置](../cache/redis-pg-cache.md).

## cache_types

所有缓存类型配置都可从此节点使用。

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

进一步了解不同 [缓存类型](../cli/manage-cache.md).

## consumers_wait_for_messages

指定如果已处理的消息数小于 `max_messages` 值。 默认值为 `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

以下选项可供使用：

- `1` — 用户继续处理来自消息队列的消息，直到到达 `max_messages` 在 `env.php` 文件，然后关闭TCP连接并终止使用者进程。 如果队列在到达 `max_messages` 值时，消费者会等待更多消息到达。

   我们建议大型商户使用此设置，因为预计会有持续的消息流，并且处理的延迟不是理想的。

- `0` — 用户处理队列中的可用消息，关闭TCP连接并终止。 即使已处理的消息数少于 `max_messages` 在 `env.php` 文件。 这有助于防止因消息队列处理中的较长延迟而导致的cron作业问题。

   我们建议较小的商户不要求持续的消息流，并且希望节省计算资源，以换取在几天内没有消息时出现轻微的处理延迟。

## cron

为商务应用程序启用或禁用cron作业。 默认情况下，将启用cron作业。 要禁用这些功能，请将 `cron` 配置 `env.php` 并将值设置为 `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>禁用cron作业时要小心。 禁用后，将不运行商务应用程序所需的基本流程。

详细了解 [克龙](../cli/configure-cron-jobs.md).

## 加密

商务使用加密密钥来保护密码和其他敏感数据。 此键值在安装过程中生成。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

详细了解 [加密密钥](https://docs.magento.com/user-guide/system/encryption-key.html) 在 _Commerce用户指南_.

## db

此节点中提供了所有数据库配置。

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

为消息队列定义默认连接。 值可以是 `db`, `amqp`，或自定义队列系统，如 `redismq`. 如果您指定 `db`，则必须先安装和配置消息队列软件。 否则，将无法正确处理消息。

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

如果 `queue/default_connection` 在系统中指定 `env.php` 文件，此连接将用于系统中所有消息队列，除非在 `queue_topology.xml`, `queue_publisher.xml` 或 `queue_consumer.xml` 文件。
例如，如果 `queue/default_connection` is `amqp` in `env.php` 但 `db` 连接在模块的队列配置XML文件中指定，模块将使用MySQL作为消息代理。

## 目录

可选目录映射选项，当Web服务器配置为从 `/pub` 目录 [改进安全性](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## 可下载域

此节点中可用的可下载域的列表。 可以使用CLI命令添加、删除或列出其他域。

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

详细了解 [可下载的域](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## 安装

Commerce应用程序的安装日期。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## 锁

使用 `lock` 节点。

详细了解 [锁定提供程序配置](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

可以在此节点中配置部署模式。

```conf
'MAGE_MODE' => 'developer'
```

详细了解 [应用程序模式](../cli/set-mode.md).

## 队列

此节点中提供了消息队列配置。

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

详细了解 [消息队列][message-queue].

## 资源

此节点中提供了资源配置设置。

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## 会话

会话配置存储在 `session` 节点。

```conf
'session' => [
  'save' => 'files'
],
```

详细了解 [会话](../storage/sessions.md).

## x-frame-options

x-frame-options标头可以使用此节点进行配置。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

详细了解 [x-frame-options](../security/xframe-options.md).

## 系统

使用此节点，Commerce会锁定 `env.php` ，然后在管理员中禁用该字段。

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

在 [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
