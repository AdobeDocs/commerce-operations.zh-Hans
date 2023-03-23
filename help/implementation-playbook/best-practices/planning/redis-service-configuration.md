---
title: Redis服务配置的最佳实践
description: 了解如何使用Adobe Commerce的扩展Redis缓存实施来提高缓存性能。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 92faa85b51a1fd5314a5906e8650b03723118ce1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Redis服务配置的最佳实践

- 使用扩展的Redis缓存实施，该实施包括以下优化，以最大限度地减少对来自Adobe Commerce的每个请求执行的Redis查询数：
   - 缩小Redis和Adobe Commerce之间网络数据传输的规模
   - 通过提高适配器自动确定需要加载的内容的能力，降低CPU周期的Redis消耗
   - 减少Redis写操作的争用情况
- 将Redis缓存与Redis会话分开
- 压缩Redis缓存并使用 `gzip` 提高性能

## 扩展Redis缓存实施

更新您的配置以使用扩展的Redis缓存实施 `\Magento\Framework\Cache\Backend\Redis`.

### 配置云部署

通过设置 `REDIS_BACKEND` 部署变量 `.magento.env.yaml` 配置文件。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

有关详细信息，请参阅 [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 变量描述 _云基础架构商务指南_.

>[!NOTE]
>
> 检查 `ece-tools` 在本地环境中使用 `composer show magento/ece-tools` 命令。 如有必要， [更新至最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>做 _not_ 使用 [扩展架构](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). 这会导致Redis连接错误。 请参阅 [Redis配置指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 在 _云基础架构上的商务_ 的双曲余切值。

### 配置内部部署

对于Adobe Commerce本地部署，请使用 `bin/magento:setup` 中。 有关说明，请参阅 [默认缓存使用Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## 单独的缓存和会话实例

将Redis缓存与Redis会话分离后，您可以单独管理缓存和会话，以防止缓存问题影响会话。

1. 更新 `.magento/services.yaml` 配置文件。

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

1. 更新 `.magento.app.yaml` 配置文件。

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 提交 [Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 更改Pro生产和暂存环境中的Redis服务配置。 包含更新的 `.magento/services.yaml` 和 `.magento.app.yaml` 配置文件。

1. 验证新实例是否正在运行，并记下端口号。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. 将端口号添加到 `.magento.env.yaml` 配置文件。

   >[!NOTE]
   >`disable_locking` 必须设置为 `1`.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. 从 [缺省数据库](../../../configuration/cache/redis-pg-cache.md) (`db 0`)。

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

在部署过程中，您应会在 [生成和部署日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
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

使用缓存压缩，但请注意，与客户端性能存在权衡。 如果有备用CPU，请启用它。 请参阅 [将Redis用于会话存储](../../../configuration/cache/redis-session.md).

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
- [将Redis用于会话存储](../../../configuration/cache/redis-session.md)
