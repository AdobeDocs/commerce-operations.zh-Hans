---
title: Realpath缓存大小
description: 了解如何通过更新PHP Readlpath缓存配置以使用推荐的设置来优化Adobe Commerce性能。
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%
---
# Realpath缓存配置最佳实践

Realpath缓存会缓存引用的文件名的实际文件系统路径，而不是每次都查找它们。 每次执行各种文件功能或需要使用文件并使用相对路径时，PHP都必须查找该文件真正存在的位置。

要提高Commerce性能，请使用以下推荐的设置来配置`php.ini`文件中的`realpath_cache`设置：

- 将缓存大小设置为10 MB (`realpath_cache_size=10M`)
- 将生存时间(ttl)设置为7200秒(`realpath_cache_ttl=7200`)

有关配置说明，请参阅[如何设置PHP选项](../../../installation/prerequisites/php-settings.md#how-to-set-php-options)。

## 受影响的产品和版本

- Adobe Commerce内部部署，所有版本2.3.x及更高版本
- 云基础架构上的Adobe Commerce，所有版本2.3.x及更高版本

## 潜在的性能影响

如果Realpath缓存配置值太低或太高，则在生成缓存时会增加额外的开销，从而减慢性能。

## 其他信息

- [内部部署：PHP设置](../../../performance/software.md#php-settings)
- 在云基础架构上：
  - [数据库最佳实践](database-on-cloud.md)
  - [Magento Commerce Cloud中最常见的数据库问题](../maintenance/resolve-database-performance-issues.md)
- [索引器“按计划更新”可优化Magento性能](../maintenance/indexer-configuration.md)
