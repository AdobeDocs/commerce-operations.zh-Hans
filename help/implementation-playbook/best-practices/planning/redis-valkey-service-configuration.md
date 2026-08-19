---
title: Valkey和Redis服务配置的最佳实践
description: 了解如何在Cloud上为Adobe Commerce配置Redis和Valkey缓存，包括副本连接、二级缓存、过时缓存和会话存储。
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
badgePaas: label="Commerce on Cloud" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于云项目上的Adobe Commerce 。"
nudge: true
autotag-review: '2026-08-18T23:34:12.845Z'
TQID: 'https://experienceleague.adobe.com/kYuQylZb2r7ElWP1oRJbyIt9jsZMhoO9yFpBMDlf1tw'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
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
source-git-commit: 55f36b56b5d719ace064eccf42675cd8f9b7683b
workflow-type: tm+mt
source-wordcount: 3304
ht-degree: 0%

---


# Valkey和Redis服务配置的最佳实践

在云部署上为Adobe Commerce配置Redis或Valkey以进行Adobe Commerce应用程序缓存、会话存储和L2缓存时，请使用这些建议。

有关Adobe Commerce本地缓存配置，请参阅用于性能优化的[二级缓存配置](/help/configuration/cache/level-two-cache.md)。

>[!NOTE]
>
>本主题介绍Commerce应用程序缓存和会话后端。 HTTP全页缓存（如Fastly或Varnish）是单独的缓存层，并且是独立配置的。 对应用程序缓存后端的更改不会替换或配置HTTP全页缓存。

这些建议涵盖以下内容：

- 选择支持的缓存服务
- 启用复制副本连接
- 单独的缓存和会话实例
- 配置缓存压缩
- 启用异步释放
- 启用多线程I/O
- 增加客户端超时和重试次数
- 配置二级缓存，包括预加载密钥、过时的缓存和[!DNL Symfony]二级缓存
- 查看配置示例

## 选择支持的缓存服务

| Adobe Commerce版本 | 推荐的缓存服务 | 二级缓存实施 |
| ---------------------- | -------------------------- | ------------------------ |
| 2.4.8及更早版本（当受确切版本支持时） | Redis或Valkey | remotesynchronizedcache |
| 2.4.9及更高版本 | Valkey | symfony_l2 |

在Adobe Commerce 2.4.9以及系统要求指定了Valkey的修补程序版本中，缓存配置不支持Redis。 始终验证[缓存后端选项和存储引用](/help/configuration/cache/cache-options.md)和[系统要求](/help/installation/system-requirements.md)中的确切Commerce版本、修补程序级别和服务版本。

>[!NOTE]
>
>验证您使用的是最新版本的`ece-tools`包。 如果不能，[请升级到最新版本](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)。 您可以使用`composer show magento/ece-tools` CLI命令检查本地环境中安装的版本。

## 启用复制副本连接

在`.magento.env.yaml`文件中启用副本连接。 此更改允许Adobe Commerce在继续使用主端点进行写入的同时，使用额外的缓存连接进行读取。 此配置可以减少主缓存服务的读取负载，并更有效地分配读取流量。

>[!NOTE]
>
>副本连接是否可用取决于项目的拓扑（例如，单节点与拆分或HA体系结构）和`ece-tools`版本。 在依赖此设置之前，通过运行`echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp`并检查`USE_SLAVE_CONNECTION`条目来确认您的服务存在副本关系。 要确认您的拓扑是否设置副本终结点，请升级`ece-tools`并重新部署，如果没有`USE_SLAVE_CONNECTION`条目，请联系Adobe Commerce支持。
>
>对于`symfony_l2`，通过`ece-tools`和云修补程序更新提供副本连接支持。 除了更改`VALKEY_USE_SLAVE_CONNECTION: true`之外，不需要其他缓存配置。 更新到最新的`ece-tools`版本以接收修复。

>[!BEGINTABS]

>[!TAB Valkey配置]

对于Valkey，请使用：

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

有关环境变量配置详细信息，请参阅《云基础架构上的Commerce指南》_中的[VALKEY_ USE_SLAVE_CONNECTION_。](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection)

>[!TAB Redis配置]

对于Redis ，使用：

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

有关环境变量配置详细信息，请参阅《云基础架构上的Commerce指南》_中的[REDIS_ USE_SLAVE_CONNECTION_。](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection)

>[!ENDTABS]

## 单独的缓存和会话实例

缓存和会话配置是相互独立的。 无论使用哪个缓存后端或二级缓存实现，`SESSION_CONFIGURATION`都不会影响缓存行为。 将缓存与会话分开允许您单独管理它们。 它减少了缓存和会话流量之间的争用，防止与缓存相关的压力影响会话，并允许每个Redis或Valkey实例针对其自身的工作负载进行调整和调整。

>[!IMPORTANT]
>
>在生产环境和暂存环境中预配专用会话实例并不是自助式的。 它需要提交包含您更新的`.magento/services.yaml`和`.magento.app.yaml`文件的[Adobe Commerce支持票证](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)，如下面的步骤3中所述。

要为会话配置专用实例，请执行以下步骤：

>[!BEGINTABS]

>[!TAB Valkey]

1. 更新`.magento/services.yaml`配置文件，将`<version>`替换为您正在使用的服务版本。 按版本查看支持的服务版本的[系统要求](/help/installation/system-requirements.md)。

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   valkey:
     type: valkey:<version>
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
     disk: 2048
   ```

1. 更新`.magento.app.yaml`配置文件。

   ```yaml
   relationships:
     database: "mysql:mysql"
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 请求一个专用于生产和暂存环境会话的新Valkey实例。

   提交[Adobe Commerce支持票证](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)。 包括更新的`.magento/services.yaml`和`.magento.app.yaml`配置文件。

   此更新不会导致任何停机时间，但需要部署才能激活新服务。

1. 验证新实例是否正在运行，并记下端口号。

   ```shell
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 将端口号添加到`.magento.env.yaml`配置文件。

   >[!IMPORTANT]
   >
   >仅当`ece-tools`无法从`MAGENTO_CLOUD_RELATIONSHIPS` Valkey会话服务定义中自动检测端口时，才配置Valkey会话端口。

   >[!NOTE]
   >
   >将`disable_locking`设置为`1`以获得最佳性能。 在极少数情况下，如果由于并发会话活动频繁而出现争用情况，请将其设置为`0`以启用锁定。

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. 从Valkey缓存实例上的[默认数据库](/help/configuration/cache/redis-pg-cache.md) (`db 0`)中删除会话。

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB 红色]

1. 更新`.magento/services.yaml`配置文件，将`<version>`替换为您正在使用的服务版本。

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   redis:
     type: redis:<version>
   
   redis-session: # This is for the new Redis instance
     type: redis:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
     disk: 2048
   ```

1. 更新`.magento.app.yaml`配置文件。

   ```yaml
      relationships:
        database: "mysql:mysql"
        redis: "redis:redis"
        redis-session: "redis-session:redis"   # Relationship of the new Redis instance
        search: "search:elasticsearch"
        rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 请求专用于生产和暂存环境会话的新Redis实例。

   提交[Adobe Commerce支持票证](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)。 包括更新的`.magento/services.yaml`和`.magento.app.yaml`配置文件。

   此更新不会导致任何停机时间，但需要部署才能激活新服务。

1. 验证新实例是否正在运行，并记下端口号。

   ```shell
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 将端口号添加到`.magento.env.yaml`配置文件。

   >[!IMPORTANT]
   >
   >仅当`ece-tools`无法从`MAGENTO_CLOUD_RELATIONSHIPS` Redis会话服务定义中自动检测Redis会话端口时，才配置该端口。

   >[!NOTE]
   >
   >将`disable_locking`设置为`1`以获得最佳性能。 在极少数情况下，如果由于并发会话活动频繁而出现争用情况，请将其设置为`0`以启用锁定。

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. 从Redis缓存实例上的[默认数据库](/help/configuration/cache/redis-pg-cache.md) (`db 0`)中删除会话。

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## 缓存压缩

如果您使用的Redis或Valkey `maxmemory`超过6 GB，则可以启用缓存压缩以减少密钥占用的空间。 请注意，此设置通过提升客户端性能来节省内存。 如果您有空闲的CPU容量，请考虑启用它。 请参阅&#x200B;_配置指南_&#x200B;中的[对会话存储使用Redis](/help/configuration/cache/redis-session.md)或[对会话存储使用Valkey](/help/configuration/cache/valkey-session.md)。

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## 启用异步释放

要在Adobe Commerce云基础架构上启用`lazyfree`，请提交[Adobe Commerce支持票证](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)，请求将以下Redis或Valkey配置应用于您的环境：

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

启用`lazyfree`后，Redis或Valkey将内存回收卸载到后台线程以进行逐出、过期、服务器启动的删除、用户删除和副本数据集刷新。 这减少了主线程阻塞，并可降低请求延迟。

>[!NOTE]
>
>`lazyfree-lazy-user-del yes`选项使`DEL`命令的行为与`UNLINK`类似，它会立即取消链接键并异步释放其内存。

>[!WARNING]
>
>由于释放发生在后台，因此由已删除、已过期或已收回的键使用的内存将保持分配状态，直到后台线程完成工作。 如果Redis或Valkey实例已处于内存紧张状态，请谨慎测试并考虑首先降低内存压力。 例如，如上所述，为特定案例禁用块缓存，并为单独缓存和会话Redis实例禁用块缓存。

## 启用多线程I/O

要在Adobe Commerce云基础架构上启用Redis I/O线程，请提交请求以下I/O线程配置的[Adobe Commerce支持票证](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)。 此配置可以通过从主线程卸载套接字读取、写入和命令解析来提高吞吐量，但代价是较高的CPU使用率。 在加载下验证并监视主机。

>[!BEGINTABS]

>[!TAB 为Redis配置I/O线程]

对于Redis：

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB 为Valkey配置I/O线程]

对于Valkey：

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]

>[!NOTE]
>
>I/O线程仅并行客户端I/O和解析。 Redis命令的执行仍保持单线程状态。

>[!WARNING]
>
>启用I/O线程可能会增加CPU的使用量，并且不会使每个工作负载受益。 从保守的值和基准开始。 如果延迟增加或CPU饱和，请减少`io-threads`或禁用I/O线程中的读取。

## 增加客户端超时和重试次数

通过调整`.magento.env.yaml`中的后端选项，将Redis或Valkey缓存客户端的容忍度提高到较短的饱和期。

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

这些设置可以通过重试连接设置并允许Redis或Valkey提供更多时间进行回复，来减少短时间尖峰期间的间歇性连接和读取超时错误。

>[!NOTE]
>
>这些设置有助于缓解短暂的拥塞，但无法修复持续性过载。

## 配置L2缓存

通过在`.magento.env.yaml`配置文件中设置`VALKEY_BACKEND`或`REDIS_BACKEND`部署变量来配置L2缓存。

在云基础架构上，有两个L2缓存实施可用于Adobe Commerce。

- 旧版实施使用`RemoteSynchronizedCache`和`Cm_Cache_Backend_File`作为本地存储
- 新式实施使用`symfony_l2`，遵循PSR-6并提高了性能。 现代实施仅支持Valkey。

| Commerce版本 | 使用Valkey的RemoteSynchronizedCache | 推荐的配置 |
| -------------- | ----------------------------------- | ------------------------- |
| 2.4.8及更早版本<br>（如果支持Valkey） | 支持的旧版L2路径 | `VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'` |
| 2.4.9及更高版本 | 不支持 | `VALKEY_BACKEND: 'symfony_l2'` |

>[!IMPORTANT]
>
>Adobe Commerce 2.4.9或更高版本的2.4.5-p16、2.4.6-p14、2.4.7-p9和2.4.8-p4修补程序不支持Redis缓存。 在不支持Redis的缓存配置中使用Valkey。 按版本查看支持的缓存服务的[系统要求](/help/installation/system-requirements.md)。

>[!BEGINTABS]

>[!TAB Valkey配置]

在支持Valkey的Commerce 2.4.8及更早版本上，使用此配置：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

在Commerce 2.4.9及更高版本上，对[!DNL Symfony] L2实现使用以下配置：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: 'symfony_l2'
```

>[!TAB Redis配置]

在支持Redis的版本2.4.8和更早版本的Commerce上，使用：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

有关环境配置详细信息，请参阅《云基础架构上的Commerce指南》_中的[`REDIS_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend)_。

>[!ENDTABS]

### 迁移到具有[!DNL Symfony]二级缓存的Valkey

如果您要将Cloud项目上的现有Adobe Commerce从`RemoteSynchronizedCache` （Redis或Valkey）迁移到`symfony_l2`，请在更新`.magento.env.yaml`之前查看以下内容。

- **更改部署变量足以启用`symfony_l2`。** 仅设置`VALKEY_BACKEND: symfony_l2`会自动生成完整的L2缓存配置。 您无需手动重新创建您以前使用的`RemoteSynchronizedCache`配置的`backend_options`结构。 请参阅[配置 [!DNL Symfony] 二级缓存](#configure-symfony-l2-cache)。

- **从现有配置中删除`preload_keys`。** 如果`RemoteSynchronizedCache`配置在`CACHE_CONFIGURATION`下包含`preload_keys`，请在迁移过程中将其删除。 有关详细信息，请参阅[预加载密钥](#preload-keys)。

- **过时的缓存行为自动更改。** 在`symfony_l2`下，`ece-tools`自动启用常用缓存类型（如`layout`、`block_html`、`full_page`和`translate`）的过时缓存，而不需要`RemoteSynchronizedCache`所需的手动前端配置。 如果您之前手动配置了过时的缓存，并且希望保留确切的先前行为，请在迁移前查看[启用过时的缓存](#enable-stale-cache)。

- **压缩需要一个显式标志。** 如果您通过`CACHE_CONFIGURATION`自定义`symfony_l2`压缩，仅设置`compression_lib`不会启用压缩 — 还必须设置`compress_data`。 请参阅[缓存压缩](#cache-compression)。

- **Redis不是`symfony_l2`支持的远程后端。** 作为此更改的一部分，请迁移到Valkey。 请参阅[设置Valkey服务](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/valkey)。

- **会话配置不受此迁移的影响。** `SESSION_CONFIGURATION`独立于缓存后端，在迁移到`symfony_l2`时不需要更改。 请参阅[单独的缓存和会话实例](#separate-cache-and-session-instances)。

>[!IMPORTANT]
>
>不要在`app/etc/env.php`中手动配置`symfony_l2`。 通过`.magento.env.yaml`对其进行配置，以便`ece-tools`在部署期间应用和维护设置。 请参阅[配置 [!DNL Symfony] 二级缓存](#configure-symfony-l2-cache)。

### 预加载键

如果您使用正确的位置（`backend_options`或`remote_backend_options`下），可以将预加载键应用于`symfony_l2`配置。 但是，Adobe不建议将预加载密钥与`symfony_l2`一起使用。 `symfony_l2`预加载实现一次提取一个键，因此它不会像对`RemoteSynchronizedCache`那样减少往返次数，并且它可以增加Valkey上的负载而不会影响性能。

预载功能允许您提供Magento在请求期间首次访问时在单个管道中获取的常用键列表。 然后，Magento会将获取的值保留在PHP内存中，以供该请求的其余部分使用，这减少了到Redis或Valkey的重复往返次数，并且可以提高这些键的请求引导性能。

您可以通过监控Redis或Valkey上的活动命令来识别常用键：

预加载密钥在`.magento.env.yaml`配置文件中配置。 此示例显示支持`RemoteSynchronizedCache`的Adobe Commerce 2.4.8及更早版本的配置。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

要列出这些键，请运行以下命令：

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

10秒后，按&#x200B;**Ctrl+C**。然后运行以下命令：

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

此日志列出了可以预加载的键。 要查看键的内容，请运行以下命令：

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

### 启用过时的缓存

陈旧缓存是二级缓存功能，它允许Adobe Commerce从`/dev/shm`提供现有的本地缓存值，而另一个请求已在重新生成同一条目。 这样可以防止并发请求等待。 这减少了在重新生成昂贵的高速缓存条目期间出现的高速缓存踩踏和锁争用。

对于Adobe Commerce 2.4.9及更高版本，在`.magento.env.yaml`文件中设置`VALKEY_BACKEND: symfony_l2`：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
```

`ece-tools`自动生成`default`前端和`stale_cache_enabled`前端，并将以下缓存类型映射到已启用过时的前端： `layout`、`block_html`、`reflection`、`config_integration`、`config_integration_api`、`full_page`和`translate`。 这些类型不需要手动`use_stale_cache`或前端配置。 此自动映射本身就是启用选择性过时缓存的一个示例。 只有特定的缓存类型使用支持过时的前端，而不是所有前端。 若要自定义哪些类型映射到`stale_cache_enabled`，或添加超出默认值的类型，请参阅[自定义 [!DNL Symfony] 二级缓存配置](#customize-the-symfony-l2-cache-configuration)。

>[!NOTE]
>
>`full_page`缓存类型与Cloud基础架构项目上的Adobe Commerce无关，因为它们使用Fastly进行全页缓存。 因此，此部分中的手动配置示例省略了`full_page`，即使`ece-tools`将其包含在默认`symfony_l2`映射中。

以下旧版配置适用于Adobe Commerce 2.4.8及更早版本，这些版本使用`RemoteSynchronizedCache`，需要手动进行过时缓存和前端配置。 这里也适用同样的“选择而非全局”建议。

#### 旧版RemoteSynchronizedCache后端的工作方式

使用`RemoteSynchronizedCache`，Magento维护每个缓存条目的两个副本： `/dev/shm`中的本地副本以及Redis或Valkey中的远程副本。 当远程副本不可用且已存在该键的重新生成锁定时，并发请求可以接收先前的本地值，而不是等到写入新值时再接收。

要为2.4.8及更早版本启用过时缓存，请在`.magento.env.yaml`文件中对其进行配置。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!WARNING]
>
>上述配置在`default`缓存前端上启用过时的缓存，这会将过时的缓存行为应用于使用该前端的所有缓存条目。 使用此设置，Magento核心缓存类型可按预期工作。 但是，如果您的项目包含自定义代码或扩展，这些代码或扩展通过通用`\Magento\Framework\App\Cache` API（例如`$this->cache->save()`）写入缓存而没有专用缓存前端，则这些条目也可以在重新生成期间提供过时的值。
>
>
>如果这会导致自定义设置中出现意外行为，请将`default`前端上的过时缓存保留为禁用状态，并仅对选定的缓存类型启用它，如下所示。

#### 分别为每个缓存类型启用过时缓存（旧版）

您只能通过在`.magento.env.yaml`中定义专用缓存前端并将所选缓存类型映射到所选缓存类型来启用过时缓存。 此手动方法适用于旧版`RemoteSynchronizedCache`后端；`symfony_l2`自动执行此映射，如上所述。

要正常工作，必须将自定义前端定义为`CACHE_CONFIGURATION.frontend`下的完整前端。 仅为新前端名称定义`use_stale_cache: true`是不够的。

**配置示例**

对于2.4.8及更早版本的Redis，以下配置为`layout`、`reflection`、`config_integration`、`config_integration_api`和`translate`缓存类型启用过时的缓存，而其他使用默认前端且禁用过时的缓存：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!NOTE]
>
>如果源前端配置了其他后端选项，请将这些选项复制到`stale_cache_enabled`，以便新前端保持相同的行为。

### 配置[!DNL Symfony]二级缓存

Adobe Commerce 2.4.9及更高版本支持`symfony_l2`缓存后端。 `symfony_l2`后端是Adobe Commerce用来管理L1和L2缓存行为的缓存实现。 **它不会将Redis或Valkey替换为远程缓存服务。**

>[!IMPORTANT]
>
>通过`.magento.env.yaml`部署变量配置`symfony_l2`，以便`ece-tools`在部署期间应用和维护设置。 请勿在`app/etc/env.php`中手动配置`symfony_l2`，因为部署可能会覆盖手动`env.php`更改。 如果`ece-tools`不应用`symfony_l2`，则Commerce可能会回退到基于文件的缓存，这可能会增加磁盘I/O、在多节点环境中增加文件系统复制开销并降低性能。

要将`symfony_l2`缓存用于Adobe Commerce 2.4.9，请完成以下步骤：

- 确保云项目使用[`ece-tools`包v2002.2.12](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)或更高版本。

- 在`.magento.env.yaml`文件中设置部署变量： `VALKEY_BACKEND`=`symfony_l2`。

  ```yaml
  stage:
    deploy:
      VALKEY_BACKEND: symfony_l2
  ```

将`VALKEY_BACKEND`部署变量设置为`symfony_l2`将自动根据Valkey服务连接详细信息（包括`default`和`stale_cache_enabled`前端）构建完整的二级缓存配置，并且已映射通用缓存类型。 定义`CACHE_CONFIGURATION`是可选的，仅在要自定义特定的后端选项时才需要。

>[!NOTE]
>
>适用于Adobe Commerce 2.4.9的修补程序ACP2E-5132通过优化标记存储、添加过时的缓存重新生成锁定，以及修复过时的标记成员资格、冗余远程写入和基于一级大小的逐出(`cleanup_percentage`)等问题而提高了[!DNL Symfony]二级缓存的性能和可靠性。 这减少了磁盘I/O和后端负载，同时提高了缓存一致性。 请参阅&#x200B;_Adobe Commerce配置指南_&#x200B;中的[增强的Symfony L2缓存性能和可靠性](/help/configuration/cache/level-two-cache.md#enhanced-symfony-l2-cache-performance-and-reliability)。
>
>该修补程序包含在Commerce包[&#128279;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)的Cloud修补程序中（依赖于`ece-tools`），并在您更新到最新的`ece-tools`版本时在部署期间自动应用。 更新到`ece-tools`的最新版本以接收修补程序。

#### 自定义[!DNL Symfony]二级缓存配置

`ece-tools`自动派生`default`和`stale_cache_enabled`前端的Valkey连接详细信息(`server`、`port`、`database`、`serializer`、`compression_lib`、`persistent_id`)。 要自定义其他后端选项（如本地缓存目录），请将`CACHE_CONFIGURATION`与`VALKEY_BACKEND: symfony_l2`一起定义为`_merge: true`。 您在此处定义的值将覆盖相应的自动生成的默认值；任何忽略的选项将继续使用`ece-tools`自动导出的值。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1
        stale_cache_enabled:
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1_stale
            use_stale_cache: true
```

>[!CAUTION]
>
>为`symfony_l2`定义`CACHE_CONFIGURATION`时，仅当有意指向项目的Valkey服务以外的缓存终结点时，才覆盖`server`或`port`。 `ece-tools`包自动从您的Valkey服务关系派生这些值。
>
>如果您覆盖`server`，则在连接到项目的Valkey服务时，其值必须为`localhost`。 提供不正确的`server`或`port`值会导致部署失败，并出现缓存连接错误。

### Adobe Commerce Cloud的二级缓存内存大小

二级缓存使用[临时文件系统](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`)作为其存储机制。 与专门的键值存储不同， tmpfs没有键逐出策略，因此内存使用量可能会无限制地增长。 为防止内存耗尽，当使用率达到可配置的阈值（默认为95%）时，Adobe Commerce会自动清除L2存储空间。 您可以通过请求更大的`/dev/shm`装载或降低清理阈值来控制内存消耗。

根据您的项目要求调整最大L2高速缓存内存使用率。 使用以下方法之一：

- 要调整`/dev/shm`装载大小，请创建支持票证。 对于这种情况，Adobe建议将`/dev/shm`装载大小设置为15 GB。
- 在应用程序级别调整`cleanup_percentage`属性，以限制存储使用量，并释放可用于其他服务的内存。
您可以在缓存配置组`cache/frontend/default/backend_options/cleanup_percentage`下的部署配置中调整配置。

>[!NOTE]
>
>`cleanup_percentage`可配置选项是在Adobe Commerce 2.4.4中引入的。

以下示例显示了`.magento.env.yaml`文件中的配置代码：

>[!BEGINTABS]

>[!TAB Valkey配置]

对于Commerce 2.4.9及更高版本，请使用以下配置将清理阈值设置为90%：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB Redis配置]

对于Commerce 2.4.8及更早版本，使用以下配置将清理阈值设置为90%：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!ENDTABS]

缓存要求因您的项目配置和自定义第三方代码而异。 设置二级高速缓存内存的大小，使高速缓存能够在没有频繁阈值命中的情况下运行。

理想情况下，二级缓存内存的使用量稳定在阈值以下，以避免频繁的存储清除。

通过运行以下CLI命令并查看`/dev/shm`行，可以检查群集的每个节点上的L2缓存存储内存使用情况。

```shell
df -h /dev/shm
```

使用情况因节点而异，但会收敛到类似的值。

## 配置示例

使用以下示例作为Redis或Valkey服务配置的起点。


### 应用所有最佳实践建议

>[!BEGINTABS]

>[!TAB Valkey配置示例]

对于`VALKEY_BACKEND: symfony_l2`，让`ece-tools`生成`default`和`stale_cache_enabled`前端及其缓存类型映射。 不要在广泛`default`前端上设置`use_stale_cache`。 下面的`CACHE_CONFIGURATION`块仅包含显式后端选项覆盖。

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture.
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            connect_retries: 3                # Number of connection retries
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Redis配置示例]

对Adobe Commerce 2.4.8及更早版本上的Redis使用以下配置：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### 按缓存类型分隔陈旧缓存

>[!BEGINTABS]

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            connect_retries: 3
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB 红色]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

>[!MORELIKETHIS]
>
>- [设置Valkey服务](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/valkey)
>- [设置Redis服务](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/redis)
>- [部署变量](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)
