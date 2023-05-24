---
title: OPcache内存大小的最佳实践
description: 描述如何通过Adobe Commerce项目上的OPcache内存消耗的特定设置避免性能下降。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Adobe Commerce中OPcache内存大小的最佳实践

对于Adobe Commerce on cloud infrastructure Pro计划架构2.3.x，建议设置 `opcache.memory_consumption` 到至少2 GB，以避免性能下降。

## 受影响的产品和版本

* Adobe Commerce on cloud infrastructure Pro计划架构2.3.x
* PHP 7.0及更高版本

## 配置内存

至少分配 **2GB** 内存的 [OPcache PHP模块](https://www.php.net/manual/en/book.opcache.php). OPcache模块配置于 `php.ini` 文件。 要分配2048 MB的内存，请设置 `opcache.memory_consumption = 2048`.

## 其他信息

* [性能最佳实践 — PHP设置](../../../performance/software.md#php-settings)
* [配置PHP选项](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [云基础架构上Adobe Commerce的数据库最佳实践](database-on-cloud.md)
* [Adobe Commerce中有关云基础架构的最常见数据库问题](../maintenance/resolve-database-performance-issues.md)
* [索引器“按计划更新”可优化Adobe Commerce性能](../maintenance/indexer-configuration.md)
