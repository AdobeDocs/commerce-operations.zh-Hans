---
title: 产品属性配置最佳实践
description: 了解如何通过限制产品属性、属性选项和属性集的数量来优化Adobe Commerce性能
role: User, Admin
feature: Best Practices
feature-set: Commerce
exl-id: 81783a4c-bc82-4733-bee3-0154cf03079a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# 产品属性配置的最佳实践

- 为获得最佳性能，配置的产品属性或产品属性选项数量不能超过建议的最大值。

- **产品属性**—
   - 对于Adobe Commerce版本2.3.x和2.4.0到2.4.1-p1，请配置不超过500个属性
   - 对于Adobe Commerce版本2.4.2及更高版本，最多配置1500个产品属性
- **产品属性选项** — 为每个属性配置最多100个属性选项
- **产品属性集** — 配置最多1000个属性集_

>[!NOTE]
>
>产品属性指定全局应用于所有产品的功能。 产品属性选项是用于指定适用于特定产品的功能的定制设置。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 减少产品属性的数量

为了在管理员管理产品和检索店面中的产品数据时获得最佳性能：

- 为不同的产品使用不同的产品模板（属性集）。
- 利用自定义选项和复杂产品进行变体管理
- 最大限度地减少可搜索属性的数量。
- 删除未使用的产品属性。
- 在外部产品管理系统(PMS)中存储和管理非商业相关属性。

## 减少产品属性选项的数量

为了在管理员管理产品和检索店面中的产品数据时获得最佳性能：

- 使用不同的变体机制创建产品：复杂的产品，自定义选项作为产品变体的来源。
- 使用定位属性和选项构建特定的产品模板，以避免广义的产品模板和选项容器。
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

1. 删除任何未使用的属性集。

## 潜在的性能影响

配置多个 **产品属性** 增加每个产品（EAV结构）的产品模板大小以及必须检索的数据量。 此增长会以下列方式影响运营：

- 与EAV数据检索和处理的数据量相关的SQL查询流量增加，从而导致DB吞吐量降低
- 显着增加Adobe Commerce索引和全文搜索索引的大小
- 在为超大产品模板构建FLAT索引时达到严格的MySQL限制，并且无法使用

产品数据和索引大小的增加可能会以下列方式影响网站性能：

- 提高了大多数与目录浏览、搜索（快速和高级）和分层导航相关的店面方案的响应时间。
- 管理员中的产品管理操作显着缓慢，这可能导致超时。
- 可以阻止“产品成批活动”功能。
- 由于执行时间较长，无法每天为大中型目录执行索引重新构建时间。

配置多个 **属性选项** 会以下列方式影响站点性能：

- 在包含复杂产品的产品详细信息(PDP)和类别页面上请求和渲染的时间较长。
- 管理产品保存操作响应时间超过最佳性能目标。
- 增加了“产品编辑”表单渲染时间。
- 结账缓慢。

## 其他信息

- [产品属性概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [属性集](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [创建产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [自定义教程>自定义产品创建表单](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)
