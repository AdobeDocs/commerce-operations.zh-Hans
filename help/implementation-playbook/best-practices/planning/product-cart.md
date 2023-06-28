---
title: 产品购物车最佳实践
description: 了解如何通过限制购物车中的产品数量来优化Adobe Commerce性能。
role: User
feature: Best Practices, Shopping Cart
exl-id: 7ea5acc2-f6b2-4244-8c07-c71fd54a18a0
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 产品购物车管理的最佳实践

为获得最佳性能，请使用以下准则来管理Adobe Commerce和Magento Open Source的购物车限制：

- 对于版本2.3.x - 2.4.2，购物车中最多允许100个产品。
- 对于版本2.4.3及更高版本，对销售规则功能的增强将购物车数量上限增加到750个。


对于版本2.3.x - 2.4.2，基于购物车项目限制的预期性能为：

- 最多 **100** 购物车中的产品 — 产品可工作，满足响应时间的性能目标。
- 最多 **300** 购物车中的产品 — 产品有效，但响应时间超过目标。
- 以上 **500** 购物车中的产品 — 不能保证购物车和结帐流程正常工作

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 减少购物车项目数量

使用以下策略管理购物车项目的数量

- 通过使用 [!UICONTROL Add Item by SKU] 功能。
- 仅添加加载项目列表所需的自定义逻辑和购物车自定义。

## 潜在的性能影响

购物车中产品数量超过建议的最大数量可能会以下列方式影响网站性能：

- 缩短了数据检索操作、验证购物车商品、检查是否应用价格规则以及计税和总计计算的响应时间。
- 提高了微型画呈现的响应时间，包括呈现购物车视图、结帐流程和执行等。
- 增加了所有存在微型艺术品的网站页面的加载时间。

## 其他信息

- [配置产品选项](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [管理购物车](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
