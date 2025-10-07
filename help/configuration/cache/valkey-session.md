---
title: 使用Valkey进行会话存储
description: 了解如何在Adobe Commerce中为会话存储配置Valkey。 了解设置步骤、配置选项和性能优化技术。
feature: Configuration, Cache
exl-id: 986ddb5c-8fc5-4210-8a41-a29e3a7625b7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 1%

---


# 使用Valkey进行会话存储

>[!IMPORTANT]
>
>您必须[安装Valkey](config-valkey.md#install-valkey)，然后才能继续。

Adobe Commerce提供了命令行选项来配置Valkey会话存储。

运行`setup:config:set`命令并指定Valkey特定的参数。

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-<parameter_name>=<parameter_value>...
```

- `--session-save=valkey`启用Valkey会话存储。 如果已启用此功能，请忽略此参数。

- `--session-save-valkey-<parameter_name>=<parameter_value>`是配置会话存储的参数/值对列表：


>[!NOTE]
>
>从&#x200B;**Adobe Commerce 2.4.9-alpha2**&#x200B;开始，**Valkey**&#x200B;已正式替换CLI工具中的Redis，因为授权发生了更改。 Valkey是Redis的一个分支，可维护几乎相同的功能。 对于&#x200B;**版本2.4.8和更早版本**，用于配置Valkey的CLI命令与Redis的命令相同，从而确保无缝向后兼容性并简化迁移或双环境支持。 以下示例显示了特定于Valkey的命令。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

| 命令行参数 | 参数名称 | 含义 | 默认值 |
|----------------------------------------------|--- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| session-save-valkey-host | 主机 | 完全限定的主机名、IP地址或绝对路径（如果使用UNIX套接字）。 | localhost |
| session-save-valkey-port | 端口 | Valkey服务器侦听端口。 | 6379 |
| session-save-valkey-password | 密码 | 如果Valkey服务器要求身份验证，请指定密码。 | 空 |
| session-save-valkey-timeout | timeout | 连接超时（秒）。 | 2.5 |
| session-save-valkey-persistent-id | persistent_identifier | 用于启用持久连接的唯一字符串（例如，sess-db0）。<br>[phpredis和php-fpm的已知问题](https://github.com/phpredis/phpredis/issues/70)。 |
| session-save-valkey-db | 数据库 | 唯一的Valkey数据库编号，建议使用此编号来防止数据丢失。<br><br>**重要信息**：如果对多种类型的缓存使用Valkey，则数据库编号必须不同。 建议将默认缓存数据库编号分配给`0`，将页面缓存数据库编号分配给`1`，将会话存储数据库编号分配给`2`。 | 0 |
| session-save-valkey-compression-threshold | compression_threshold | 设置为`0`以禁用压缩（建议在`suhosin.session.encrypt = On`时使用）。 | 2048 |
| session-save-valkey-compression-lib | compress_library | 选项： gzip、lzf、lz4或snappy。 | gzip |
| session-save-valkey-log-level | log_level | 设置为以下任意值，按从少到多的顺序列出：<ul><li>0（紧急：仅最严重的错误）<li>1（警报：需要立即执行操作）<li>2（严重：应用程序组件不可用）<li>3 （错误：运行时错误，不严重，但必须监控）<li>4（警告：其他信息，推荐）<li>5（注意：正常但重要的情况）<li>6（信息：信息性消息）<li>7（调试：仅供开发或测试使用的信息最多）</ul> | 1 |
| session-save-valkey-max-concurrency | max_concurrency | 可以等待一个会话锁定的最大进程数。 对于大型生产群集，请将此参数至少设置为PHP进程数的10%。 | 6 |
| session-save-valkey-break-after-frontend | break_after_frontend | 在尝试中断前端（即storefront）会话锁定之前等待的秒数。 | 5 |
| session-save-valkey-break-after-adminhtml | break_after_adminhtml | 在尝试中断Admin HTML（即管理员）会话锁定之前等待的秒数。 | 30 |
| session-save-valkey-first-lifetime | first_lifetime | 非机器人首次写入时会话的生命周期（以秒为单位），或使用`0`禁用。 | 600 |
| session-save-valkey-bot-first-lifetime | bot_first_lifetime | 机器人首次写入时会话的生命周期（以秒为单位），或使用`0`禁用。 | 60 |
| session-save-valkey-bot-lifetime | bot_lifetime | 后续写入时机器人会话的生命周期（以秒为单位），或使用`0`禁用。 | 7200 |
| session-save-valkey-disable-locking | disable_locking | 完全禁用会话锁定。 | 0（假） |
| session-save-valkey-min-lifetime | min_lifetime | 最短会话生命周期（以秒为单位）。 | 60 |
| session-save-valkey-max-lifetime | max_lifetime | 最长会话生命周期（以秒为单位）。 | 2592000 （720小时） |
| session-save-valkey-sentinel-master | sentinel_master | Valkey Sentinel主名称。 | 空 |
| session-save-valkey-sentinel-servers | sentinel_servers | Valkey Sentinel服务器列表，以逗号分隔。 | 空 |
| session-save-valkey-sentinel-verify-master | sentinel_verify_master | 验证Valkey Sentinel主状态标志。 | 0（假） |
| session-save-valkey-sentinel-connect-retries | sentinel_connect_retries | Sentinels的连接重试。 | 5 |

## 示例

以下示例将Valkey设置为会话数据存储，将主机设置为`127.0.0.1`，将日志级别设置为`4`，并将数据库编号设置为`2`。 所有其他参数均设置为默认值。

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-host=127.0.0.1 --session-save-valkey-log-level=4 --session-save-valkey-db=2
```

>[!NOTE]
>
>从&#x200B;**Adobe Commerce 2.4.9**&#x200B;开始，**Valkey**&#x200B;已正式替换CLI工具中的Redis，因为授权发生了更改。 Valkey是Redis的一个分支，可维护几乎相同的功能。 对于&#x200B;**版本2.4.8和更早版本**，用于配置Valkey的CLI命令与Redis的命令相同，从而确保无缝向后兼容性并简化迁移或双环境支持。 以下示例显示了特定于Valkey的命令。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 结果

Commerce向`<magento_root>app/etc/env.php`添加类似于以下内容的行：

```php
'session' => [
    'save' => 'valkey',
    'redis' => [
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000',
    ],
],
```

>[!INFO]
>
>会话记录的TTL使用Cookie生命周期的值，该值可在管理员中进行配置。 如果Cookie生命周期设置为`0` （默认值为`3600`），则Valkey会话将在min_lifetime中指定的秒数内过期（默认值为`60`）。 此差异是由于Valkey和会话Cookie对`0`的生命周期值的解释方式不同所致。 如果不希望出现这种行为，请增加min_lifetime的值。

## 验证Valkey连接

要验证Valkey和Commerce是否正常工作，请登录到运行Valkey的服务器，打开终端，然后使用`valkey-cli monitor`命令或`redis-cli ping`命令。

### Valkey monitor命令

```bash
valkey-cli monitor
```

会话存储输出示例：

```
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Valkey ping命令

```bash
valkey-cli ping
```

预期的响应为： `PONG`。

如果两个命令都成功，则Valkey设置正确。

### 检查压缩数据

为了检查压缩的会话数据和页面缓存，[RESP.app](https://flathub.org/apps/app.resp.RESP)支持Commerce 2会话和页面缓存的自动解压缩，并以人类可读的格式显示PHP会话数据。
