---
title: env.php参考
description: 查看env.php文件的值列表。
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 26fac37405ad635f297b65415517451d5149e50f
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 0%

---

# env.php参考

`env.php`文件包含以下部分：

| 名称 | 描述 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 管理区域的设置 |
| `cache` | 配置redis页面和默认缓存 |
| `cache_types` | 缓存存储设置 |
| `consumers_wait_for_messages` | 配置使用者处理消息队列中消息的方式 |
| `cron` | 启用或禁用cron作业 |
| `crypt` | 加密函数的加密密钥 |
| `db` | 数据库连接设置 |
| `default_connection` | 消息队列默认连接 |
| `directories` | Commerce目录映射设置 |
| `downloadable_domains` | 可下载域列表 |
| `install` | 安装日期 |
| `lock` | 锁定提供程序设置 |
| `MAGE_MODE` | [应用程序模式](../bootstrap/application-modes.md) |
| `queue` | [消息队列](../queues/manage-message-queues.md)设置 |
| `resource` | 将资源名称映射到连接 |
| `session` | 会话存储数据 |
| `system` | 禁用字段以在管理员中进行编辑 |
| `x-frame-options` | [x-frame-options][x-frame-options]的设置 |

## 后端

使用env.php中的&#x200B;**节点为Commerce管理员URL配置** frontName`backend`。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## 缓存

使用`cache`文件中的`env.php`节点配置redis页面和默认缓存。

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

在[Redis配置](../cache/redis-pg-cache.md)中了解详情。

## 缓存类型

此节点提供所有缓存类型配置。

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

了解有关不同[缓存类型](../cli/manage-cache.md)的更多信息。

## consumers_wait_for_messages

指定当处理的消息数小于`max_messages`值时，使用者是否应继续轮询消息。 默认值为`1`。

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

可以使用以下选项：

- `1` — 使用者继续处理来自消息队列的消息，直到达到`max_messages`文件中指定的`env.php`值为止，然后关闭TCP连接并终止使用者进程。 如果队列在达到`max_messages`值之前清空，则使用者将等待更多消息到达。

  我们建议大型商家使用此设置，因为预计消息流量会持续不变，并且不希望出现处理延迟。

- `0` — 使用者处理队列中的可用消息，关闭TCP连接并终止。 即使已处理的消息数小于`max_messages`文件中指定的`env.php`值，使用者也不会等待其他消息进入队列。 这有助于防止由于消息队列处理长时间延迟而导致cron作业出现问题。

  我们建议将此设置用于小型商家，他们不希望持续发送消息流，并且更愿意节省计算资源以换取在连续几天没有消息的情况下出现的轻微处理延迟。

## cron

启用或禁用Commerce应用程序的cron作业。 默认情况下，将启用cron作业。 要禁用它们，请将`cron`配置添加到`env.php`文件并将值设置为`0`。

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>禁用cron作业时要小心。 禁用后，Commerce应用程序所需的基本进程将无法运行。

了解有关[Crons](../cli/configure-cron-jobs.md)的更多信息。

## 加密

Commerce使用加密密钥保护密码和其他敏感数据。 此密钥在安装过程中生成。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

在[Commerce用户指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/security/encryption-key)中了解有关&#x200B;_加密密钥_&#x200B;的更多信息。

## db

所有数据库配置在此节点中均可用。

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

定义消息队列的默认连接。 该值可以是`db`、`amqp`或自定义队列系统，如`redismq`。 如果指定了`db`以外的任何值，则必须先安装和配置消息队列软件。 否则，将无法正确处理消息。

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

如果在系统`queue/default_connection`文件中指定了`env.php`，则此连接用于通过系统的所有消息队列，除非在`queue_topology.xml`、`queue_publisher.xml`或`queue_consumer.xml`文件中定义了特定连接。
例如，如果`queue/default_connection`在`amqp`中为`env.php`，但在模块的队列配置XML文件中指定了`db`连接，则模块将使用MySQL作为消息代理。

## 目录

可选目录映射选项，在将Web服务器配置为从`/pub`目录提供Commerce应用程序时需要设置这些选项，以提高[安全性](../../installation/tutorials/docroot.md)。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

此节点中可用的可下载域列表。 使用CLI命令可以添加、删除或列出其他域。

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

了解有关[可下载域](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd)的更多信息。

## 安装

Commerce应用程序的安装日期。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## 锁定

锁定提供程序设置是使用`lock`节点配置的。

了解有关[锁定提供程序配置](../../installation/tutorials/lock-provider.md)的详细信息。

## 图像模式

可以在此节点中配置部署模式。

```conf
'MAGE_MODE' => 'developer'
```

了解有关[应用程序模式](../cli/set-mode.md)的详细信息。

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

了解有关[消息队列][message-queue]的详细信息。

## 资源

资源配置设置在此节点中可用。

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## session

会话配置存储在`session`节点中。

```conf
'session' => [
  'save' => 'files'
],
```

了解有关[会话](../storage/sessions.md)的详细信息。

## x-frame-options

x-frame-options标头可以使用此节点进行配置。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

了解有关[x-frame-options](../security/xframe-options.md)的详细信息。

## 系统

使用此节点，Commerce在`env.php`文件中锁定配置值，然后在管理员中禁用该字段。

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

在[env-php-config-set](../cli/set-configuration-values.md)中了解详情。

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/


## 将变量添加到文件配置

您可以使用操作系统(OS)级别的环境变量来设置或覆盖每个配置选项（具有值的变量）。

`env.php`配置存储在具有嵌套级别的数组中。 要将嵌套数组路径转换为OS环境变量的字符串，请用双下划线字符`__`、大写并以`MAGENTO_DC_`为前缀连接路径中的每个键。

例如，我们将会话保存处理程序从`env.php`配置转换为操作系统环境变量。

```conf
'session' => [
  'save' => 'files'
],
```

与`__`连接，大写键将变为`SESSION__SAVE`。

然后，我们使用`MAGENTO_DC_`作为前缀以获取生成的OS环境变量名称`MAGENTO_DC_SESSION__SAVE`。

```shell
export MAGENTO_DC_SESSION__SAVE=files
```

作为另一个示例，让我们转换标量`env.php`配置选项路径。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

>[!INFO]
>
>虽然变量名称应大写，但值区分大小写，应按照文档进行保留。

我们只需将其大写并添加`MAGENTO_DC_`作为前缀，即可接收最终的OS环境变量名称`MAGENTO_DC_X-FRAME-OPTIONS`。

```shell
export MAGENTO_DC_X-FRAME-OPTIONS=SAMEORIGIN
```

>[!INFO]
>
>请注意，`env.php`内容将具有高于操作系统环境变量的优先级。

## 使用变量覆盖文件配置

要使用操作系统环境变量覆盖现有`env.php`配置选项，配置的数组元素必须经过JSON编码并设置为`MAGENTO_DC__OVERRIDE`操作系统变量的值。

设置`MAGENTO_DC__OVERRIDE`后，Commerce框架将绕过`env.php`文件中的相应值，并直接从环境变量中读取配置。 `env.php`文件中的值保持不变，但被覆盖的配置部分忽略。

>[!IMPORTANT]
>
>`MAGENTO_DC__OVERRIDE`变量完全绕过`env.php`文件中的指定配置部分。 此行为不同于单个`MAGENTO_DC_`变量，这些变量的优先级低于`env.php`文件中的值。

如果需要覆盖多个配置选项，请在JSON编码之前将它们全部组合到单个数组中。

例如，让我们覆盖以下`env.php`配置：

```conf
'session' => [
  'save' => 'files'
],
'x-frame-options' => 'SAMEORIGIN'
```

上述数组的JSON编码文本将为
`{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}`。

现在，将它设置为`MAGENTO_DC__OVERRIDE`操作系统变量的值。

```shell
export MAGENTO_DC__OVERRIDE='{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}'
```

>[!INFO]
>
>如有必要，请确保正确引用和/或转义JSON编码数组，以防止操作系统损坏编码字符串。