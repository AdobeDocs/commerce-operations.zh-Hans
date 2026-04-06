---
title: Redis和Valkey服务配置的最佳实践
description: 了解如何为Adobe Commerce配置Redis和Valkey服务。 通过二级缓存、从属连接、陈旧缓存和会话分离提高缓存性能。
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: aedff83fe473691340f0f254e7c79ef7e632ac0d
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 0%

---


# Redis和Valkey服务配置的最佳实践

使用这些建议为Adobe Commerce缓存和会话配置Redis或Valkey。

- 配置L2缓存
- 启用从属连接
- 预加载键
- 启用过时的缓存
- 将缓存和会话分开
- 压缩缓存
- 配置示例

>[!NOTE]
>
>对于云基础架构环境上的Commerce，请验证您使用的是最新版本的`ece-tools`包。 如果不能，[请升级到最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html)。 您可以使用`composer show magento/ece-tools` CLI命令检查本地环境中安装的版本。

## 配置L2缓存

通过在`REDIS_BACKEND`配置文件中设置`VALKEY_BACKEND`或`.magento.env.yaml`部署变量来配置L2缓存。

>[!BEGINTABS]

>[!TAB Redis配置]

对于Redis ，使用：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

有关云基础架构上的环境配置，请参阅《云基础架构上的Commerce指南》[`REDIS_BACKEND`中的](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend)_配置引用_。

有关内部部署安装，请参阅[配置指南](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)中的&#x200B;_配置Redis页面缓存_。

>[!TAB Valkey配置]

对于Valkey，请使用：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

有关云基础架构上的环境配置，请参阅《云基础架构上的Commerce指南》[`VALKEY_BACKEND`中的](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend)_配置引用_。

有关内部部署安装，请参阅[配置指南](../../../configuration/cache/config-valkey.md)中的&#x200B;_配置Valkey_。

>[!ENDTABS]


### Adobe Commerce Cloud的二级缓存内存大小

二级缓存使用[临时文件系统](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`)作为其存储机制。 与专门的键值存储不同， tmpfs没有键逐出策略，因此内存使用量可能会无限制地增长。 为防止内存耗尽，当使用率达到可配置的阈值（默认为95%）时，Adobe Commerce会自动清除L2存储空间。 您可以通过请求更大的`/dev/shm`装载或降低清理阈值来控制内存消耗。

根据您的项目要求调整最大L2高速缓存内存使用率。 使用以下方法之一：

- 创建支持票证以调整`/dev/shm`装载大小。 对于这种情况，Adobe建议将`/dev/shm`装载大小设置为15 GB。
- 在应用程序级别调整`cleanup_percentage`属性，以限制存储使用量，并释放可用于其他服务的内存。
您可以在缓存配置组`cache/frontend/default/backend_options/cleanup_percentage`下的部署配置中调整配置。

>[!NOTE]
>
>`cleanup_percentage`可配置选项是在Adobe Commerce 2.4.4中引入的。

以下示例显示了`.magento.env.yaml`文件中的配置代码：

>[!BEGINTABS]

>[!TAB Redis配置]

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

>[!TAB Valkey配置]

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

```bash
df -h /dev/shm
```

使用情况可能因节点而异，但应该会收敛到类似的值。

## 为L2缓存配置自定义目录

在优化二级缓存性能时，您可以选择将本地缓存文件存储在自定义的高性能目录中，如RAM磁盘(`/dev/shm/`)。

要确保应用程序范围的一致性并防止零碎的缓存存储，请在`app/etc/env.php`文件中配置特定的L2后端选项和全局目录注册表。

**最佳实践：**&#x200B;同时定义`local_backend_options['cache_dir']`和全局`directories['cache']['path']`。

- **`local_backend_options['cache_dir']`**：指示后端缓存适配器（例如，`Cm_Cache_Backend_File`）将其同步的L2缓存文件存储在指定位置。
- **`directories['cache']['path']`**：更新Adobe Commerce `DirectoryList`注册表，将自定义路径建立为整个应用程序的最终系统缓存目录。

### 防止拆分缓存目录和GlusterFS分段错误

如果在`local_backend_options`中专门定义自定义路径，则二级缓存引擎可以正常工作，但全局应用程序注册表仍会将`var/cache`识别为默认缓存位置。

此配置不匹配导致“脑分割”情况，即第三方扩展或核心回退进程将临时文件写入默认`var/cache`目录。

**对Adobe Commerce Cloud的严重影响：**&#x200B;在Pro体系结构上，`var/`目录挂载在共享的分布式文件系统上。 在此网络挂载上强制执行高速缓存I/O会超出客户端的承受能力，并且是&#x200B;**GlusterFS分段故障和群集范围中断的主要触发因素**。 配置这两个设置可确保所有缓存I/O严格保留在本地、高性能磁盘上。

### 配置示例

要强制实施单个统一缓存目录，请更新您的`env.php`文件以包含两个配置：

```php
return [
    // 1. Override the global directory registry
    'directories' => [
        'cache' => [
            'path' => '/dev/shm/magento_cache'
        ]
    ],
    // 2. Configure the L2 cache engine
    'cache' => [
        'frontend' => [
            'default' => [
                'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
                'backend_options' => [
                    'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                    'server' => '127.0.0.1',
                    'port' => '6379',
                    'database' => '1',
                    // ... other redis configurations ...
                    'local_backend' => 'Cm_Cache_Backend_File',
                    'local_backend_options' => [
                        'cache_dir' => '/dev/shm/magento_cache' 
                    ]
                ]
            ]
        ]
    ],
    // ...
];
```

## 启用从属连接

启用`.magento.env.yaml`文件中的从连接，以允许Adobe Commerce在继续使用主端点进行写入的同时使用额外的只读缓存连接进行读取。 此配置可以减少主缓存服务的读取负载，并更有效地分配读取流量。

>[!BEGINTABS]

>[!TAB Redis配置]

对于Redis ，使用：

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

有关Commerce Cloud基础架构上的环境配置，请参阅《云基础架构指南》上的[Commerce &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection)中的&#x200B;_REDIS_USE_SLAVE_CONNECTION_。

对于Adobe Commerce内部部署，请使用`bin/magento setup`命令配置新的Redis缓存实现。 请参阅[配置指南](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)中的&#x200B;_对默认缓存使用Redis_。

>[!TAB Valkey配置]

对于Valkey，请使用：

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

有关Commerce Cloud基础架构上的环境配置，请参阅《云基础架构指南》上的[Commerce &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection)中的&#x200B;_VALKEY_USE_SLAVE_CONNECTION_。

对于Adobe Commerce内部部署，请使用`bin/magento setup`命令配置新的Valkey缓存实现。 请参阅[配置指南](../../../configuration/cache/config-valkey.md)中的&#x200B;_配置Valkey_。

>[!ENDTABS]

## 预加载键

Magento通常一次从Redis或Valkey加载一个键的缓存条目。 预载功能允许您提供Magento在请求期间首次访问时在单个管道中获取的常用键列表。 然后，Magento会将获取的值保留在PHP内存中，以供该请求的其余部分使用，这减少了到Redis或Valkey的重复往返次数，并且可以提高这些键的请求引导性能。

您可以通过监控Redis或Valkey上的活动命令来识别常用键：

>[!BEGINTABS]

>[!TAB Redis预加载密钥配置]

预加载密钥在`.magento.env.yaml`配置文件中配置。

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

10秒后，按&#x200B;**[!UICONTROL Ctrl+C]**。 然后运行以下命令：

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

此日志列出了可以预加载的键。 要查看键的内容，请运行以下命令：

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

有关内部部署安装，请参阅[配置指南](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature)中的&#x200B;_Redis预加载功能_。

>[!TAB Valkey预加载密钥配置]

预加载密钥在`.magento.env.yaml`配置文件中配置。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

10秒后，按&#x200B;**[!UICONTROL Ctrl+C]**。 然后运行以下命令：

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

此日志列出了可以预加载的键。 要查看键的内容，请运行以下命令：

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

有关内部部署安装，请参阅[配置指南](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature)中的&#x200B;_Valkey预加载功能_。

>[!ENDTABS]

## 启用过时的缓存

过时的缓存是`RemoteSynchronizedCache`的二级缓存功能。 启用后，Adobe Commerce可以在另一个请求已重新生成同一条目时从`/dev/shm`提供现有的本地缓存值，而不是让每个并发请求等待。 这减少了在重新生成昂贵的高速缓存条目期间出现的高速缓存踩踏和锁争用。

### 工作原理

使用`RemoteSynchronizedCache`，Magento维护每个缓存条目的两个副本： `/dev/shm`中的本地副本以及Redis或Valkey中的远程副本。 当远程副本不可用且已存在该键的重新生成锁定时，并发请求可以接收先前的本地值，而不是等到写入新值时再接收。

要启用过时的缓存，请在`.magento.env.yaml`文件中对其进行配置。

>[!BEGINTABS]

>[!TAB 配置Redis的过时缓存]

对于Redis：

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

>[!TAB 配置Valkey的过时缓存]

对于Valkey：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>`full_page`缓存类型与Cloud基础结构项目上的Adobe Commerce无关，因为它们使用[Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)。

有关内部部署安装，请参阅[配置指南](../../../configuration/cache/level-two-cache.md#stale-cache-options)中的&#x200B;_过时缓存选项_。

>[!WARNING]
>
>上述配置在`default`缓存前端上启用过时的缓存，这会将过时的缓存行为应用于使用该前端的所有缓存条目。 使用此设置时，Magento核心缓存类型通常可按预期工作。 但是，如果您的项目包含自定义代码或扩展，这些代码或扩展通过通用`\Magento\Framework\App\Cache` API（例如`$this->cache->save()`）写入缓存而没有专用缓存前端，则这些条目也可以在重新生成期间提供过时的值。
>
>
>如果这会导致自定义设置中出现意外行为，请将`default`前端上的过时缓存保留为禁用状态，并只为选定的缓存类型启用它，就像通常的[内部部署](../../../configuration/cache/level-two-cache.md#stale-cache-options)一样。

### 逐个启用每种缓存类型的过时缓存

您只能通过在`.magento.env.yaml`中定义专用缓存前端并将所选缓存类型映射到所选缓存类型来启用过时缓存。

要正常工作，必须将自定义前端定义为`CACHE_CONFIGURATION.frontend`下的完整前端。 仅为新前端名称定义`use_stale_cache: true`是不够的。

**配置示例**

>[!BEGINTABS]

>[!TAB 配置Redis的过时缓存]

对于Redis：

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

>[!TAB 配置Valkey的过时缓存]

对于Valkey：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

>[!ENDTABS]

>[!NOTE]
>
>如果为源前端配置了其他后端选项（如压缩、重试、预加载密钥或其他优化值），请将这些选项复制到`stale_cache_enabled`，以便新前端保持相同的行为。


## 单独的缓存和会话实例

将缓存与会话分开允许您单独管理它们。 它减少了缓存和会话流量之间的争用，防止与缓存相关的压力影响会话，并允许每个Redis或Valkey实例针对其自身的工作负载进行调整和调整。

请按照以下步骤为会话配置专用实例：

>[!BEGINTABS]

>[!TAB 红色]

1. 更新`.magento/services.yaml`配置文件。

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
     type: redis:6.0
   
   search:
     type: elasticsearch:7.9
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:3.8
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

   提交[Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)。 包括更新的`.magento/services.yaml`和`.magento.app.yaml`配置文件。

   此更新不会导致任何停机时间，但需要部署才能激活新服务。

1. 验证新实例是否正在运行，并记下端口号。

   ```bash
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

1. 从Redis缓存实例上的[默认数据库](../../../configuration/cache/redis-pg-cache.md) (`db 0`)中删除会话。

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Valkey]

1. 更新`.magento/services.yaml`配置文件。

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
   search:
     type: elasticsearch:7.9
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:3.8
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

   提交[Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)。 包括更新的`.magento/services.yaml`和`.magento.app.yaml`配置文件。

   此更新不会导致任何停机时间，但需要部署才能激活新服务。

1. 验证新实例是否正在运行，并记下端口号。

   ```bash
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

1. 从Valkey缓存实例上的[默认数据库](../../../configuration/cache/redis-pg-cache.md) (`db 0`)中删除会话。

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## 缓存压缩

如果您使用的Redis或Valkey `maxmemory`超过6 GB，则可以启用缓存压缩以减少密钥占用的空间。 请注意，此设置通过提升客户端性能来节省内存。 如果您有空闲的CPU容量，请考虑启用它。 请参阅[配置指南](../../../configuration/cache/redis-session.md)中的[对会话存储使用Redis](../../../configuration/cache/valkey-session.md)或&#x200B;_对会话存储使用Valkey_。

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

要在云基础架构上的Adobe Commerce上启用`lazyfree`，请提交[Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)，请求将以下Redis或Valkey配置应用于您的环境：

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

要在云基础架构上的Adobe Commerce上启用Redis I/O线程，请提交请求以下I/O线程配置的[Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)。 此配置可以通过从主线程卸载套接字读取和写入以及命令解析来提高吞吐量，但代价是较高的CPU使用率。 在加载下验证并监视主机。

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

## 配置示例

使用以下示例作为Redis或Valkey服务配置的起点。


### 应用所有最佳实践建议

>[!BEGINTABS]

>[!TAB 红色]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
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

>[!TAB Valkey配置示例]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
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

### 应用所有最佳实践推荐，并按缓存类型分隔陈旧缓存

>[!BEGINTABS]

>[!TAB 红色]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
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
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
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

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
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
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
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
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## 其他信息

请参阅以下相关主题：

- [Redis页面缓存](../../../configuration/cache/redis-pg-cache.md)
- [使用Redis进行会话存储](../../../configuration/cache/redis-session.md)
- [将Valkey用于默认缓存](../../../configuration/cache/valkey-pg-cache.md)
- [使用Valkey进行会话存储](../../../configuration/cache/valkey-session.md)
