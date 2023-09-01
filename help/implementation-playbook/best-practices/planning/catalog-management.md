---
title: 目录管理最佳实践
description: 了解配置购物车限制和产品属性，以及列出分页、选项、促销和变体的建议。
role: Developer
feature: Best Practices, Catalog Management
source-git-commit: a81e88a4293880ae90cd531ce60c5a2b177188f2
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---


# 目录管理最佳实践

此处描述的目录管理最佳实践涵盖了一系列问题，包括（但不限于）：

- 购物车限制
- 类别限制
- 产品属性
- 产品列表分页
- 产品选项
- 产品变体
- 促销活动

## 购物车限制

为获得最佳性能，请使用以下指南来管理Adobe Commerce和Magento Open Source的购物车限制。

### 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

### 减少购物车项目数

使用以下策略管理购物车项目的数量

- 通过使用 [!UICONTROL Add Item by SKU] 功能。
- 仅添加加载项目列表所需的自定义逻辑和购物车自定义。

## 类别限制

配置大量类别可能会影响性能。

### 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

### 减少产品数量

使用以下策略减少类别的数量：

- 通过属性和自定义选项管理独特的产品功能
- 删除不活动的类别
- 优化导航中的目录深度

## 产品属性

配置过多产品属性或产品属性选项可能会影响性能。

>[!NOTE]
>
>产品属性指定全局应用于所有产品的功能。 产品属性选项是用于指定适用于特定产品的功能的定制设置。

### 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

### 减少属性数量

为了在管理员管理产品和检索店面中的产品数据时获得最佳性能：

- 为不同的产品使用不同的产品模板（属性集）。
- 利用自定义选项和复杂产品进行变体管理
- 最大限度地减少可搜索属性的数量。
- 删除未使用的产品属性。
- 在外部产品管理系统(PMS)中存储和管理非商业相关属性。

### 减少属性选项的数量

为了在管理员管理产品和检索店面中的产品数据时获得最佳性能：

- 使用不同的变体机制创建产品：复杂的产品，自定义选项作为产品变体的来源。
- 使用定位属性和选项构建特定的产品模板，以避免广义的产品模板和选项容器。
- 维护实际属性选项的列表。
- 通过外部产品管理系统(PMS)管理产品信息。

### 减少属性集的数量

使用MySQL删除未使用的产品属性集。

#### 查看属性集配置

1. [连接到站点数据库](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. 使用MySQL查找属性集数

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. 删除任何未使用的属性集。

### 潜在的性能影响

配置多个 **产品属性** 增加每个产品的产品模板大小（EAV结构）以及必须检索的数据量。 此增加会以下列方式影响操作：

- 与EAV数据检索和已处理的数据量相关的SQL查询流量增加，导致数据库吞吐量降低
- 显着增加了Adobe Commerce索引和全文搜索索引的大小
- 在为超大产品模板构建FLAT索引时达到严格的MySQL限制，并且无法使用它

产品数据和索引大小的增加可能会以下列方式影响网站性能：

- 提高了大多数与目录浏览、搜索（快速和高级）和分层导航相关的店面方案的响应时间。
- 管理员中的产品管理操作显着缓慢，这可能导致超时。
- 可以阻止“产品成批活动”功能。
- 由于执行时间较长，无法每天为中型和大型目录执行索引重新构建时间。

配置多个 **属性选项** 会以下列方式影响站点性能：

- 产品详细信息(PDP)和包含复杂产品的类别页面上的请求和渲染时间较长。
- 管理产品保存操作响应时间超过最佳性能目标。
- 增加了“产品编辑”表单渲染时间。
- 结账缓慢。

## 产品选项

为每个产品配置过多产品选项可能会影响性能。

### 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

### 减少选项数量

使用以下策略减少每个产品的产品选项数：

- 配置复杂的产品和自定义选项作为产品变体的来源。
- 使用属性集构建具有目标属性和选项的特定产品模板，而不是创建适用于所有产品的全局产品模板和选项容器。
- 通过外部产品管理系统(PMS)管理产品信息。

### 潜在的性能影响

配置多个产品选项会增加所有读取和写入操作中为每个产品检索的数据量，从而导致：

- 增加了SQL查询流量和负载 `JOIN` 操作提高了数据库吞吐量。
- 增加了Adobe Commerce索引和全文搜索索引的大小。

上面列出的增加可能会以下列方式影响站点性能：

- 与属性中包含许多选项的产品相关的大多数店面方案的响应时间更长。
- 显着增加了在“管理员”中完成产品管理操作所需的时间，这可能会导致超时，尤其是对于与属性列表和树检索（包括升级规则管理）相关的方案。
- 可以阻止完成异步批量操作的批量操作，例如导入和导出以及为共享目录中的多个产品分配自定义价格。

## 产品列表分页

每页显示的产品过多可能会影响性能。

### 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

### 更新产品列表配置

如果某个类别中有太多产品，请更新店面目录配置以禁用此选项 **允许每页所有产品**.

禁用此选项后，Adobe Commerce使用产品列表店面分页控件来管理店面组件中显示的产品数量。 有关说明，请参阅 [配置分页控件](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## 产品SKU限制

配置过多的产品SKU可能会降低产品数据检索速度并增加完成管理员操作或索引的时间，从而影响性能。

### 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

### 减少产品数量

使用以下策略减少产品数量(SKU)：

- 最小化乘数 — 
   - 整合网站会降低乘数。
   - 使用自定义定价的替代产品功能替换共享目录和客户组乘数。
   - 客户组和共享目录均用作商店中有效SKU数量的乘数。
- 重新构建目录 — 
   - 减少分配给类别的产品数量。
   - 通过减少网站、客户组、共享目录、产品或可配置产品选项的数量来减少SKU的数量
- 通过使用自定义选项而不是创建单独的产品来提供更多产品变体。
- 考虑到有效的SKU可能包括价格的一些潜在排列，因为每个商店或客户组的价格可以有不同的指定。
- 停用或删除未使用的系统组件，如模块。 请参阅  [卸载模块](../../../installation/tutorials/uninstall-modules.md).
- 在外部平台管理系统(PMS)中管理产品。

## 产品变体

为每个产品配置过多变量可能会影响性能。

### 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

### 减少变体的数量

为获得最佳网站性能，请使用以下策略减少产品变体的数量：

- 通过分发不同产品的变体数量来重构目录。
- 删除没有库存的可配置属性选项。
- 通过自定义选项、类别、相关、分组和捆绑产品等替代功能管理变体。

### 潜在的性能影响

超出建议数量的产品变体可能会以下列方式影响网站性能：

- 产品详细信息和包含复杂产品的类别页面上的请求和渲染时间较长。
- 增加了在管理员中完成保存操作的响应时间。
- 增加了呈现产品编辑表单的时间。
- 结账缓慢。

## 促销活动

按照以下最佳实践为购物车中的商品配置销售和促销活动：

- **销售规则（购物车价格规则）**
   - 管理和删除未使用的规则。
   - 添加严格的规则条件（如属性或类别过滤器）以实现最有效的匹配。
- **优惠券**
   - 删除未使用和过期的优惠券。
   - 仅生成满足促销活动要求所需的优惠券数量。

### 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

### 潜在的性能影响

如果购物车价格规则或优惠券的数量超过建议的最大数量，则会以下列方式影响网站性能：

- 将产品添加到购物车时增加的响应时间。
- 增加了加载和渲染微型艺术品的时间。
- 增加了呈现购物车页面的时间。
- 增加了呈现的时间 **总计** 在“结帐”页面上阻止。
