---
title: 为会话存储配置Redis
description: 了解如何在Adobe Commerce中为会话存储配置Redis。 了解CLI设置、会话参数和连接验证技术。
feature: Configuration, Cache
exl-id: f93f500d-65b0-4788-96ab-f1c3d2d40a38
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
autotag-review: '2026-06-22T21:56:59.687Z'
TQID: 'https://experienceleague.adobe.com/deiikp11GlXtMJFkhT7DhgguCYFkplQgr2fYm8MMN7I'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 859
ht-degree: 1%

---

# 为会话存储配置Redis

{{cloud-cache-config}}

Commerce现在提供命令行选项来配置Redis会话存储。 在以前的版本中，您编辑了`<Commerce install dir>app/etc/env.php`文件。 命令行提供验证，是推荐的配置方法，但您仍可以编辑`env.php`文件。

>[!IMPORTANT]
>
>在配置会话存储之前，必须安装[Redis](config-redis.md#install-redis)。

运行`setup:config:set`命令并指定Redis特定的参数。

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

位置

`--session-save=redis`启用Redis会话存储。 如果已启用此功能，请忽略此参数。

`--session-save-redis-<parameter_name>=<parameter_value>`是配置会话存储的参数/值对列表：

| 命令行参数 | 参数名称 | 含义 | 默认值 |
|--- |--- |--- |--- |
| session-save-redis-host | 主机 | 完全限定的主机名、IP地址或绝对路径（如果使用UNIX套接字）。 | localhost |
| session-save-redis-port | 端口 | Redis服务器侦听端口。 | 6379 |
| session-save-redis-password | 密码 | 如果Redis服务器要求身份验证，请指定密码。 | 空 |
| session-save-redis-timeout | timeout | 连接超时（秒）。 | 2.5 |
| session-save-redis-persistent-id | persistent_identifier | 用于启用持久连接的唯一字符串（例如，sess-db0）。<br>[phpredis和php-fpm的已知问题](https://github.com/phpredis/phpredis/issues/70)。 |  |
| session-save-redis-db | 数据库 | 唯一的Redis数据库编号，建议使用此编号以防止数据丢失。<br><br>**重要信息**：如果对多种类型的缓存使用Redis，则数据库编号必须不同。 建议将默认高速缓存数据库编号指定为0，将页高速缓存数据库编号指定为1，将会话存储数据库编号指定为2。 | 0 |
| session-save-redis-compression-threshold | compression_threshold | 设置为0可禁用压缩（建议在`suhosin.session.encrypt = On`时使用）。<br>[字符串大于64 KB的已知问题](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18)。 | 2048 |
| session-save-redis-compression-lib | compress_library | 选项： gzip、lzf、lz4或snappy。 | gzip |
| session-save-redis-log-level | log_level | 设置为以下任意值，按从少到多的顺序列出：<ul><li>0（紧急：仅最严重的错误）<li>1（警报：需要立即执行操作）<li>2（严重：应用程序组件不可用）<li>3 （错误：运行时错误，不严重，但必须监控）<li>4（警告：其他信息，推荐）<li>5（注意：正常但重要的情况）<li>6（信息：信息性消息）<li>7（调试：仅供开发或测试使用的信息最多）</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | 可以等待一个会话锁定的最大进程数。 对于大型生产群集，请将此参数至少设置为PHP进程数的10%。 | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | 在尝试中断前端（即storefront）会话锁定之前等待的秒数。 | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | 在尝试中断Admin HTML（即管理员）会话锁定之前等待的秒数。 | 30 |
| session-save-redis-first-lifetime | first_lifetime | 非机器人首次写入时会话的生命周期（以秒为单位），或使用0禁用。 | 600 |
| session-save-redis-bot-first-lifetime | bot_first_lifetime | 机器人首次写入时会话的生命周期（以秒为单位），或使用0禁用。 | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | 机器人后续写入会话的生命周期（以秒为单位），或使用0禁用。 | 7200 |
| session-save-redis-disable-locking | disable_locking | 完全禁用会话锁定。 | 0（假） |
| session-save-redis-min-lifetime | min_lifetime | 最短会话生命周期（以秒为单位）。 | 60 |
| session-save-redis-max-lifetime | max_lifetime | 最长会话生命周期（以秒为单位）。 | 2592000 （720小时） |
| session-save-redis-sentinel-master | sentinel_master | Redis Sentinel主名称 | 空 |
| session-save-redis-sentinel-servers | sentinel_servers | Redis Sentinel服务器列表，逗号分隔 | 空 |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | 验证Redis Sentinel主状态标志 | 0（假） |
| session-save-redis-sentinel-connect-retries | sentinel_connect_retries | Sentinels的连接重试 | 5 |

## 示例

以下示例将Redis设置为会话数据存储，将主机设置为`127.0.0.1`，将日志级别设置为4，并将数据库编号设置为2。 所有其他参数均设置为默认值。

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 结果

Commerce向`<magento_root>app/etc/env.php`添加类似于以下内容的行：

```php
'session' => [
    'save' => 'redis',
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
>会话记录的TTL使用Cookie生命周期的值，该值可在管理员中进行配置。 如果Cookie Lifetime设置为0（默认值为3600），则Redis会话将在min_lifetime中指定的秒数内过期（默认值为60）。 此差异是由于Redis和会话Cookie对生命周期值0的解释方式不同所致。 如果不希望出现这种行为，请增加min_lifetime的值。

## 验证Redis连接

要验证Redis和Commerce是否协同工作，请登录到运行Redis的服务器，打开终端，然后使用Redis monitor命令或ping命令。

### Redis监视命令

```shell
redis-cli monitor
```

会话存储输出示例：

```text
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Redis ping命令

```shell
redis-cli ping
```

`PONG`应为响应。

如果两个命令都成功，则Redis设置正确。

### 检查压缩数据

为了检查压缩的会话数据和页面缓存，[RESP.app](https://flathub.org/apps/details/app.resp.RESP)支持Commerce 2会话和页面缓存的自动解压缩，并以可读形式显示PHP会话数据。
