---
title: 产品列表分页的最佳实践
description: 了解如何通过管理店面目录每个页面上显示的产品数量来优化Adobe Commerce性能。
role: User, Admin
feature: Best Practices, Catalog Management
exl-id: 473f23a9-53fb-41a6-9b3a-af7bd1208be0
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 产品列表分页的最佳实践

为获得最佳性能，每页最多显示48个产品。

您可以将Adobe Commerce配置为允许购物者在一个页面上查看所有类别的产品。 如果类别产品的数量明显超过48个产品，请更新店面分页控件的目录配置。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 更新产品列表配置

如果您在任何类别中有超过48种产品，请更新店面目录配置以禁用该选项 **允许每页所有产品**.

禁用此选项后，Adobe Commerce使用产品列表店面分页控件来管理店面组件中显示的产品数量。 有关说明，请参阅 [配置分页控件](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## 其他信息

- [配置产品列表](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
