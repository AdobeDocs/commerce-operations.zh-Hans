---
title: Realpath缓存大小
description: 了解如何通过更新PHP Readlpath缓存配置以使用推荐的设置来优化Adobe Commerce性能。
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 1%

---

# Realpath缓存配置最佳实践

Realpath缓存会缓存引用的文件名的实际文件系统路径，而不是每次都查找它们。 每次执行各种文件功能或需要使用文件并使用相对路径时，PHP都必须查找该文件真正存在的位置。

要提高Commerce性能，请使用以下推荐的设置来配置`realpath_cache`文件中的`php.ini`设置：

- 将缓存大小设置为10 MB (`realpath cache_size=10M`)
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
