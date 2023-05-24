---
title: Realpath缓存大小
description: 了解如何通过更新PHP readlpath缓存配置以使用推荐的设置来优化Adobe Commerce性能。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Realpath缓存配置最佳实践

Realpath缓存缓存所引用文件名的实际文件系统路径，而不是每次都查找它们。 每次执行各种文件功能或需要某个文件并使用相对路径时，PHP都必须查找该文件确实存在的位置。

要提高Commerce性能，请使用以下推荐的设置来配置 `realpath_cache` 中的设置 `php.ini` 文件：

- 将缓存大小设置为10 MB (`realpath cache_size=10M`)
- 将生存时间(ttl)设置为7200秒(`realpath_cache_ttl=7200`)

有关配置说明，请参阅 [如何设置PHP选项](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## 受影响的产品和版本

- Adobe Commerce内部部署，所有版本2.3.x及更高版本
- 云基础架构上的Adobe Commerce，所有版本2.3.x及更高版本

## 潜在的性能影响

如果Realpath缓存配置值太低或太高，则会在缓存生成期间增加额外的开销，这会降低性能。

## 其他信息

- [内部部署： PHP设置](../../../performance/software.md#php-settings)
- 在云基础架构上：
   - [数据库最佳实践](database-on-cloud.md)
   - [Magento Commerce Cloud中最常见的数据库问题](../maintenance/resolve-database-performance-issues.md)
- [索引器“按计划更新”可优化Magento性能](../maintenance/indexer-configuration.md)
