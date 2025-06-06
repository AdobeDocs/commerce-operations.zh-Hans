---
title: Redis服务配置的最佳实践
description: 了解如何通过使用适用于Adobe Commerce的扩展Redis缓存实现来提高缓存性能。
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: bbebb414ae3b8c255e17b1f3673a6c4b7c6f23b2
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Redis服务配置的最佳实践

- 配置Redis二级缓存
- 启用Redis从属连接
- 预加载键
- 启用过时的缓存
- 将Redis缓存与Redis会话分离
- 压缩Redis缓存，并使用`gzip`以获得更高的压缩

## 配置Redis二级缓存

通过在`.magento.env.yaml`配置文件中设置`REDIS_BACKEND`部署变量来配置Redis二级缓存。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

有关云基础架构上的环境配置，请参阅《云基础架构上的Commerce指南》_中的[`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hans#redis_backend)_。

有关内部部署安装，请参阅&#x200B;_配置指南_&#x200B;中的[配置Redis页面缓存](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)。

>[!NOTE]
>
>验证您使用的是最新版本的`ece-tools`包。 如果不能，[请升级到最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=zh-Hans)。 您可以使用`composer show magento/ece-tools` CLI命令检查本地环境中安装的版本。


### L2高速缓存内存大小(Adobe Commerce Cloud)

二级缓存使用[临时文件系统](https://en.wikipedia.org/wiki/Tmpfs)作为存储机制。 与专用键值数据库系统相比，临时文件系统没有控制内存使用的键逐出策略。

内存使用率控制不足会导致二级缓存内存使用率随着时间增长，因为它会累积过时的缓存。

为避免内存耗尽二级缓存实现，Adobe Commerce会在达到特定阈值时清除存储。 默认的阈值为95%。

根据项目对高速缓存存储的要求，调整二级高速缓存内存的最大使用率非常重要。 使用以下方法之一配置内存高速缓存大小：

- 创建支持票证以请求`/dev/shm`装载的大小更改。
- 在应用程序级别调整`cleanup_percentage`属性，以限制存储的最大填充百分比。 剩余的可用内存可供其他服务使用。
您可以在缓存配置组`cache/frontend/default/backend_options/cleanup_percentage`下的部署配置中调整配置。

>[!NOTE]
>
>`cleanup_percentage`可配置选项是在Adobe Commerce 2.4.4中引入的。

以下代码显示了`.magento.env.yaml`文件中的示例配置：

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

缓存要求可能因项目配置和自定义第三方代码而异。 L2高速缓存内存大小的范围允许L2高速缓存在阈值命中次数不多的情况下运行。
理想情况下，二级缓存内存的使用量应该稳定在低于阈值的某个级别，只是为了避免频繁的存储清除。

您可以使用以下CLI命令检查群集的每个节点上的L2缓存存储内存使用情况，并查找`/dev/shm`行。
虽然使用情况可能因不同的节点而异，但应该会收敛到相同的值。

```bash
df -h
```

## 启用Redis从属连接

在`.magento.env.yaml`配置文件中启用Redis从属连接，以便仅允许一个节点处理读写通信，而其他节点处理只读通信。

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

请参阅《云基础架构上的Commerce指南》_中的[REDIS_USE_SLAVE_CONNECTION_。](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hans#redis_use_slave_connection)

对于Adobe Commerce内部部署，请使用`bin/magento:setup`命令配置新的Redis缓存实现。 请参阅&#x200B;_配置指南_&#x200B;中的[对默认缓存使用Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)。

>[!WARNING]
>
>请&#x200B;_不_&#x200B;为具有[缩放/拆分架构](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html?lang=zh-Hans)的云基础架构项目配置Redis从属连接。 这会导致Redis连接错误。 请参阅&#x200B;_云基础架构上的Commerce_&#x200B;指南中的[Redis配置指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hans#redis_use_slave_connection)。

## 预加载键

要在页面之间重用数据，请在`.magento.env.yaml`配置文件中列出预加载的密钥。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

有关内部部署安装，请参阅&#x200B;_配置指南_&#x200B;中的[Redis预加载功能](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature)。

## 启用过时的缓存

通过使用过时的缓存，同时并行生成新缓存，减少锁定等待时间并提高性能，在处理大量块和缓存键时尤其如此。 在`.magento.env.yaml`配置文件中启用过时的缓存并定义缓存类型：

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

>[!NOTE]
>
>在上一个示例中，`full_page`缓存与云基础架构项目上的Adobe Commerce无关，因为它们使用[Fastly](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/fastly)。

有关配置内部部署安装的信息，请参阅&#x200B;_配置指南_&#x200B;中的[过时缓存选项](../../../configuration/cache/level-two-cache.md#stale-cache-options)。

## 单独的Redis缓存和会话实例

通过将Redis缓存与Redis会话分离，您可以单独管理缓存和会话。 它可防止缓存问题影响会话，从而可能影响收入。 每个Redis实例都在自己的核心上运行，这可以提高性能。

1. 更新`.magento/services.yaml`配置文件。

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
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

1. 提交[Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=zh-Hans#submit-ticket)以请求配置专用于生产和暂存环境会话的新Redis实例。 包括更新的`.magento/services.yaml`和`.magento.app.yaml`配置文件。 这不会导致任何停机，但需要部署来激活新服务。

1. 验证新实例是否正在运行，并记下端口号。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 将端口号添加到`.magento.env.yaml`配置文件。

   >[!IMPORTANT]
   >
   >仅当`ece-tools`无法从`MAGENTO_CLOUD_RELATIONSHIPS` redis会话服务定义中自动检测该端口时才配置redis会话端口。

   >[!NOTE]
   >
   >`disable_locking`必须设置为`1`。

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374 # check the port in $MAGENTO_CLOUD_RELATIONSHIPS and put it here (by default, you can delete this line!!)
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. 从Redis缓存实例上的[默认数据库](../../../configuration/cache/redis-pg-cache.md) (`db 0`)中删除会话。

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

在部署期间，您应该会在[生成和部署日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=zh-Hans#build-and-deploy-logs)中看到以下行：

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## 缓存压缩

如果您使用的是超过6GB的Redis `maxmemory`，则可以使用缓存压缩来减少密钥占用的空间。 请注意，需要权衡客户端性能。 如果您有备用CPU，请启用它。 请参阅&#x200B;_配置指南_&#x200B;中的[为会话存储](../../../configuration/cache/redis-session.md)使用Redis。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## 其他信息

- [Redis页面缓存](../../../configuration/cache/redis-pg-cache.md)
- [使用Redis进行会话存储](../../../configuration/cache/redis-session.md)
