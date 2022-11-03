---
title: 产品列表分页的最佳实践
description: 了解如何通过管理店面目录每个页面上显示的产品数量来优化Adobe Commerce性能。
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# 产品列表分页的最佳实践

为获得最佳性能，每页最多显示48个产品。

您可以配置Adobe Commerce，以允许购物者在单个页面上查看所有类别产品。 如果类别产品数量显着超过48个产品，请更新店面分页控件的目录配置。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 更新产品清单配置

如果任何类别中的产品超过48个，请更新storefront目录配置，以禁用 **每页允许所有产品**.

禁用此选项后，Adobe Commerce会使用产品清单店面分页控件来管理店面组件中显示的产品数量。 有关说明，请参阅 [配置分页控件](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## 其他信息

- [配置产品列表](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
