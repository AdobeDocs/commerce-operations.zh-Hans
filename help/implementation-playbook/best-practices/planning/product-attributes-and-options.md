---
title: 产品属性配置最佳实践
description: 了解如何通过限制产品属性、属性选项和属性集的数量来优化Adobe Commerce性能
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# 产品属性配置的最佳实践

- 为获得最佳性能，请勿配置超过建议的最大产品属性数或产品属性选项数。

- **产品属性**—
   - 对于Adobe Commerce版本2.3.x和2.4.0到2.4.1-p1，请配置不超过500个属性
   - 对于Adobe Commerce版本2.4.2及更高版本，请最多配置1500个产品属性
- **产品属性选项** — 为每个属性配置最多100个属性选项
- **产品属性集** — 配置最多1000个属性集_

>[!NOTE]
>
>产品属性指定可全局应用于所有产品的功能。 产品属性选项是用于指定适用于特定产品的功能的自定义设置。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 减少产品属性的数量

为了在从管理员管理产品和检索店面中的产品数据时获得最佳性能：

- 对不同产品使用不同的产品模板（属性集）。
- 利用自定义选项和复杂的产品进行变体管理
- 最大限度地减少可搜索属性的数量。
- 删除未使用的产品属性。
- 在外部产品管理系统(PMS)中存储和管理与非商务相关的属性。

## 减少产品属性选项的数量

为了在从管理员管理产品和检索店面中的产品数据时获得最佳性能：

- 使用不同的变体机制创建产品：复杂产品，自定义选项作为产品变体的来源。
- 使用定向属性和选项构建特定产品模板，以避免使用通用的产品模板和选项容器。
- 维护实际属性选项的列表。
- 通过外部产品管理系统(PMS)管理产品信息。

## 减少产品属性集的数量

使用MySQL删除未使用的产品属性集。

### 查看属性集配置

1. [连接到站点数据库](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. 使用MySQL查找属性集的数量

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. 删除所有未使用的属性集。

## 潜在的性能影响

配置多个 **产品属性** 增加每个产品（EAV结构）的产品模板大小和必须检索的数据量。 此增加会通过以下方式影响操作：

- 与EAV数据检索相关的SQL查询流量增加，以及处理的数据量，这会导致数据库吞吐量降低
- Adobe Commerce索引和全文搜索索引的大小显着增加
- 在为超大的产品模板构建FLAT索引并且无法使用它时，达到MySQL的严格限制

产品数据和索引大小的增加可能会通过以下方式影响网站性能：

- 增加了与目录浏览、搜索（快速和高级）以及分层导航相关的大多数店面情景的响应时间。
- 管理员中的产品管理操作速度显着放缓，可能会导致超时。
- 可以阻止“产品批量操作”功能。
- 由于执行时间过长，无法每天执行中型和大型目录的索引重建时间。

配置多个 **属性选项** 会影响网站性能的方法如下：

- 产品详细信息(PDP)和包含复杂产品的类别页面上的请求和渲染时间较长。
- 管理员产品保存操作响应时间增加到超出最佳性能目标。
- 增加产品编辑表单渲染时间。
- 结帐缓慢。

## 其他信息

- [产品属性概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [属性集](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [创建产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [自定义教程>自定义产品创建表单](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)

