---
title: Redis服务配置的最佳实践
description: 了解如何使用Adobe Commerce 2.3.5的扩展Redis缓存实施来提高缓存性能。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 12de523cc7ea1486c894d54efe6944d92d87ded0
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Redis服务配置的最佳实践

- 对于在云基础架构上部署的Adobe Commerce 2.3.3及更高版本，请升级到Redis版本5.0。
- 对于Adobe Commerce版本2.3.5或更高版本，请使用扩展的Redis缓存实施。 此实施包括以下优化，以最大限度地减少对来自Adobe Commerce的每个请求执行的Redis查询数：
   - 减小Redis和Adobe Commerce之间网络数据传输的大小
   - 通过提高适配器自动确定需要加载的内容的能力，降低CPU周期的Redis消耗
   - 减少Redis写操作的争用情况

## 受影响的产品和版本

Adobe Commerce云基础架构，版本为2.3.3或更高版本。
Adobe Commerce（所有部署方法）、版本2.3.5及更高版本

## 为云部署更新Redis版本

对于使用Adobe Commerce 2.3.3或更高版本的云基础架构上的Adobe Commerce部署，请将Redis服务升级到Redis版本5.0。有关说明，请参阅Adobe Commerce云基础架构文档中的以下主题：

- [设置Redis服务](https://devdocs.magento.com/cloud/project/services-redis.html)
- [更改服务版本](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## 配置扩展的Redis缓存实施

对于Adobe Commerce 2.3.5及更高版本，请更新您的配置以使用扩展的Redis缓存实施 `\Magento\Framework\Cache\Backend\Redis`.

### 云部署配置

使用 `ece-tools` 2002.1.1或更高版本，通过设置 `REDIS_BACKEND` 环境配置文件中的部署变量， `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

有关详细信息，请参阅 [部署变量> `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) (位于云基础架构的Adobe Commerce文档中)。

>[!NOTE]
>
> 使用 `composer show magento/ece-tools` 命令。 如有必要， [更新ece-tools版本](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

>[!WARNING]
>
>做 _not_ 使用 [扩展架构](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). 这会导致Redis连接错误。 请参阅 [Redis配置指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 在 _云基础架构上的商务_ 的双曲余切值。


### 内部部署配置

对于Adobe Commerce本地部署，请使用 `bin/magento:setup` 中。 有关说明，请参阅 [默认缓存使用Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## 其他信息

- [Adobe Commerce v2.3.5 — 性能提升](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [Redis页面缓存](../../../configuration/cache/redis-pg-cache.md)


