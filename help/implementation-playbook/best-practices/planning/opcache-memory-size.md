---
title: OPcache内存大小的最佳实践
description: 介绍如何避免因Adobe Commerce项目上OPcache内存消耗的特定设置而导致性能下降。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Adobe Commerce中OPcache内存大小的最佳实践

对于云基础架构上的Adobe Commerce Pro计划架构2.3.x，建议设置 `opcache.memory_consumption` 至少2 GB，以避免性能下降。

## 受影响的产品和版本

* Adobe Commerce云基础架构Pro计划架构2.3.x
* PHP 7.0及更高版本

## 配置内存

至少分配 **2 GB** 内存 [OPcache PHP模块](https://www.php.net/manual/en/book.opcache.php). OPcache模块在 `php.ini` 文件。 要分配2048 MB的内存，请设置 `opcache.memory_consumption = 2048`.

## 其他信息

* [性能最佳实践 — PHP设置](../../../performance/software.md#php-settings)
* [配置PHP选项](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [云基础架构上的Adobe Commerce数据库最佳实践](database-on-cloud.md)
* [Adobe Commerce中云基础架构上最常见的数据库问题](../maintenance/resolve-database-performance-issues.md)
* [索引器“按计划更新”可优化Adobe Commerce性能](../maintenance/indexer-configuration.md)
