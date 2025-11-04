---
title: Valkey服务配置的最佳实践
description: 了解如何通过使用适用于Adobe Commerce的扩展Valkey缓存实现来提高缓存性能。
role: Developer, Admin
feature: Best Practices, Cache
exl-id: ca1598b0-07c6-4338-aed1-f2ba05375197
source-git-commit: 75dc606da65196619028e99ec44841db3988a73e
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Valkey服务配置的最佳实践

Adobe建议在配置Valkey服务时遵循以下最佳实践：

## 配置Valkey L2缓存

通过在`VALKEY_BACKEND`配置文件中设置`.magento.env.yaml`部署变量来配置Valkey L2缓存。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

有关云基础架构上的环境配置，请参阅《云基础架构上的Commerce指南》[`VALKEY_BACKEND`中的](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend)__。

有关内部部署安装，请参阅[配置指南](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching)中的&#x200B;_配置Valkey页缓存_。

>[!NOTE]
>
>验证您使用的是最新版本的`ece-tools`包。 如果不能，[请升级到最新版本](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)。 您可以使用`composer show magento/ece-tools` CLI命令检查本地环境中安装的版本。

### 二级缓存内存大小(Adobe Commerce Cloud)

二级缓存使用[临时文件系统](https://en.wikipedia.org/wiki/Tmpfs)作为存储机制。 与专用键值数据库系统相比，临时文件系统没有控制内存使用的键逐出策略。

内存使用率控制不足会导致二级缓存内存使用率随着时间增长，因为它会累积过时的缓存。

为避免内存耗尽二级缓存实现，Adobe Commerce会在达到特定阈值时清除存储。 默认的阈值为95%。

根据项目对高速缓存存储的要求，调整二级高速缓存内存的最大使用率非常重要。 使用以下方法之一配置内存高速缓存大小：

- 创建支持票证以请求`/dev/shm`装载的大小更改。
- 在应用程序级别调整`cleanup_percentage`属性，以限制存储的最大填充百分比。 剩余的可用内存可供其他服务使用。
您可以在缓存配置组`cache/frontend/default/backend_options/cleanup_percentage`下的部署配置中调整配置。

>[!NOTE]
>
>Adobe Commerce 2.4.4中引入了`cleanup_percentage`配置选项。

以下示例显示了`CACHE_CONFIGURATION`文件中的`.magento.env.yaml`：

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

缓存要求可能因项目配置和自定义第三方代码而异。 L2高速缓存内存大小调整范围允许L2高速缓存运行而不发生不必要的阈值命中。
理想情况下，二级缓存内存的使用量应该稳定在低于阈值的某个级别，以避免频繁的存储清除。

您可以使用以下CLI命令检查群集的每个节点上的L2缓存存储内存使用情况，然后搜索`/dev/shm`行。
虽然使用情况可能因不同的节点而异，但应该会收敛到相同的值。

```bash
df -h
```

## 启用Valkey从属连接

在`.magento.env.yaml`配置文件中启用Valkey从连接，以便仅允许一个节点处理读写通信，而其他节点处理只读通信。

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

有关更多详细信息，请参阅《云基础架构上的Commerce指南》[中的](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection)VALKEY_USE_SLAVE_CONNECTION _。_

对于Adobe Commerce内部部署，请使用`bin/magento:setup`命令配置新的Valkey缓存实现。 有关详细信息，请参阅[配置指南](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching)中的&#x200B;_将值键用于默认缓存_。

>[!WARNING]
>
>请&#x200B;_不_&#x200B;为具有[缩放/拆分架构](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture)的云基础架构项目配置Valkey从属连接。 这会导致Valkey连接错误。 有关详细信息，请参阅[Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection)指南中的&#x200B;_Valkey配置指南_。

## 预加载键

要在页面之间重用数据，请在`.magento.env.yaml`配置文件中列出预加载的密钥。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

有关内部部署安装，请参阅[配置指南](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature)中的&#x200B;_Valkey预加载功能_。

## 启用过时的缓存

通过使用过时的缓存并同时生成新缓存，减少锁等待时间并提高性能，在处理大量块和缓存键时尤其如此。 在`.magento.env.yaml`配置文件中启用过时缓存并定义缓存类型：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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
>在上一个示例中，`full_page`缓存与云基础架构项目上的Adobe Commerce无关，因为它们使用[Fastly](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/cdn/fastly)。

有关配置内部部署安装的信息，请参阅[配置指南](../../../configuration/cache/level-two-cache.md#stale-cache-options)中的&#x200B;_过时缓存选项_。

在部署期间，您应该会在[生成和部署日志](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/test/log-locations#build-and-deploy-logs)中看到以下行：

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## 缓存压缩

如果您使用的Valkey `maxmemory`超过6GB，则可以使用缓存压缩来减少密钥占用的空间。 请注意，需要权衡客户端性能。 如果您有备用的CPU，Adobe建议启用它们。 请参阅[配置指南](../../../configuration/cache/valkey-session.md)中的&#x200B;_对会话存储使用Valkey_。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```
