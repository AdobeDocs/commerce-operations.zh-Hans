---
title: 产品车最佳实践
description: 了解如何通过限制购物车中的产品数量来优化Adobe Commerce性能。
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# 产品车管理最佳实践

为获得最佳性能，请使用以下准则来管理Adobe Commerce和Magento Open Source的购物车限制：

- 对于版本2.3.x - 2.4.2，购物车中最多允许100个产品。
- 对于版本2.4.3及更高版本，对销售规则功能的增强将购物车最大数量增加到750。


对于版本2.3.x - 2.4.2，基于购物车项目限制的预期性能为：

- 最高 **100** 购物车中的产品 — 产品可正常工作，满足响应时间的性能目标。
- 最高 **300** 购物车中的产品 — 产品有效，但响应时间会增长到高于目标。
- 以上 **500** 购物车中的产品 — 购物车和结账流程无法保证有效

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 减少购物车项目数

使用以下策略来管理购物车项目的数量

- 使用 [!UICONTROL Add Item by SKU] 功能。
- 仅添加加载项目列表所需的自定义逻辑和购物车自定义。

## 潜在的性能影响

购物车中产品数量超过建议的最大数量可能会通过以下方式影响网站性能：

- 增加了数据检索操作、验证购物车项目、检查是否应用价格规则以及税和总计计算的响应时间。
- 增加了小型图表渲染的响应时间，包括渲染购物车视图、结帐流程和执行。
- 缩短了所有存在小型机的网站页面的加载时间。

## 其他信息

- [配置产品选项](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [管理购物车](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
