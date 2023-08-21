---
title: 产品限制最佳实践
description: 了解配置产品库存单位(SKU)以最大化网站性能的最佳实践。
role: Admin
feature: Best Practices, Catalog Management
exl-id: 37af7b92-05ac-4a4f-9009-11e8d9f95c2f
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# 产品SKU配置的最佳实践

为了最大化性能，建议的有效产品库存单位(SKU)的最大值为2.42亿。 此有效产品SKU最大值计算如下：

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

其中：

- N表示该类别的项目数
- 客户组包括共享目录，因为它会创建一个额外的客户组。

有效SKU的数量超过最大数量会减慢产品数据检索的速度，并增加完成管理员面板操作或索引的时间。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 减少产品数量

使用以下策略减少产品数量(SKU)：

- 最小化乘数 — 
   - 整合网站会降低乘数。 如果您有50,000个SKU、10个网站和10个客户组，则SKU的有效数量为500万。 删除5个客户组将有效SKU减少到250万。
   - 使用自定义定价的替代产品功能替换共享目录和客户组乘数。
   - 客户组和共享目录均用作商店中有效SKU数量的乘数。
- 重新构建目录 — 
   - 减少分配给类别的产品数量。
   - 通过减少网站、客户组、共享目录、产品或可配置产品选项的数量来减少SKU的数量
- 通过使用自定义选项而不是创建单独的产品来提供更多产品变体。
- 考虑到有效的SKU可能包括价格的一些潜在排列，因为每个商店或客户组的价格可以有不同的指定。
- 停用或删除未使用的系统组件，如模块。 (请参阅  [卸载模块](../../../installation/tutorials/uninstall-modules.md).)
- 在外部平台管理系统(PMS)中管理产品。

## 其他信息

- [创建产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [产品分配](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [使用共享目录](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- 云基础架构： [设置多个网站和商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- 内部部署： [多个网站或商店](../../../configuration/multi-sites/ms-overview.md)
- [云基础架构上的Adobe Commerce：存储配置的最佳实践](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
