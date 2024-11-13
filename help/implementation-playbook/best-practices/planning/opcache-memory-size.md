---
title: OPcache内存大小的最佳实践
description: 描述如何通过Adobe Commerce项目上的OPcache内存消耗的特定设置避免性能下降。
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 6c0a9268cb3a3b2e76f4a389846e8407f0893b4f
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---

# Adobe Commerce中OPcache内存大小的最佳实践

对于云基础架构上的Adobe Commerce Pro计划架构2.3.x，建议将`opcache.memory_consumption`设置为至少2 GB，以避免性能下降。

## 受影响的产品和版本

* Adobe Commerce on cloud infrastructure Pro计划架构2.3.x
* PHP 7.0及更高版本

## 配置内存

为[OPcache PHP模块](https://www.php.net/manual/en/book.opcache.php)分配至少&#x200B;**2GB**&#x200B;的内存。 已在`php.ini`文件中配置OPcache模块。 要分配2048 MB的内存，请设置`opcache.memory_consumption = 2048`。

## 其他信息

* [性能最佳实践 — PHP设置](../../../performance/software.md#php-settings)
* [配置PHP选项](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/configure-app-yaml)
* [云基础架构上Adobe Commerce的数据库最佳实践](database-on-cloud.md)
* [Adobe Commerce中有关云基础架构的最常见数据库问题](../maintenance/resolve-database-performance-issues.md)
* [索引器“按计划更新”可优化Adobe Commerce性能](../maintenance/indexer-configuration.md)
