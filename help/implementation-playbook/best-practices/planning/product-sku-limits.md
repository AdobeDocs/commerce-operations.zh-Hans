---
title: 产品限制最佳实践
description: 了解配置产品库存单位(SKU)以最大化网站性能的最佳实践。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 3a187ae8c066e56df0d7f4981d26ffb934f64576
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# 产品SKU配置的最佳实践

为了最大限度地提高性能，建议有效的产品库存保存件数(SKU)的最大值为2.42亿。 此有效产品最大值的计算方式为：

```text
Effective SKU = N\[SKUs\] * Stores/Websites * Customer Groups
```

超过最大有效SKU数量会减慢产品数据检索速度，并增加完成管理员操作的时间。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 减少产品数量

请使用以下策略来减少产品(SKU)的数量：

- 最小化乘数 — 
   - 移动存储或网站会降低乘数。 如果您有50,000个SKU、10个网站和10个客户组，则SKU的有效数量为500万。 删除五个客户组会将有效SKU减少到250万。
   - 为自定义定价使用替代产品功能来替换共享目录和客户组乘数。
- 重构目录 — 
   - 减少分配给类别的产品数量。
   - 通过减少商店、网站、客户组或产品数量来减少SKU数量。
- 使用自定义选项而不是创建单独的产品来提供更多产品变体。
- 停用或删除未使用的系统组件，如模块。 (请参阅  [卸载模块](../../../installation/tutorials/uninstall-modules.md).)
- 在外部平台管理系统(PMS)中管理产品。

## 其他信息

- [创建产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [产品分配](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- 云基础架构： [设置多个网站和商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- 本地： [多个网站或商店](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce云基础架构：存储配置最佳实践](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
