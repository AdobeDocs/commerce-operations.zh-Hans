---
title: 配置促销活动的最佳实践
description: 了解配置销售规则和优惠券代码以优化Commerce商店性能的最佳实践。
role: User
feature: Best Practices, Price Rules, Shopping Cart
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 配置促销活动的最佳实践

要获得最佳性能，请按照以下最佳实践为购物车中的商品配置销售和促销活动：

- **销售规则（购物车价格规则）** — 为所有网站配置不超过1000个购物车价格规则
   - 管理和删除未使用的规则。
   - 添加严格的规则条件（如属性或类别过滤器）以实现最有效的匹配。
- **优惠券**—
   - 验证数据库中的优惠券总数是否小于250,000。
   - 删除未使用和过期的优惠券。
   - 仅生成满足促销活动要求所需的优惠券数量。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 潜在的性能影响

如果购物车价格规则或优惠券的数量超过建议的最大数量，则会以下列方式影响网站性能：

- 将产品添加到购物车时增加的响应时间。
- 增加了加载和渲染微型艺术品的时间。
- 增加了呈现购物车页面的时间。
- 增加了呈现的时间 **总计** 在“结帐”页面上阻止。
- 应用优惠券可能需要超过2秒的时间。

## 其他信息

- [了解营销活动和促销活动](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [购物车价格规则](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [教程：创建购物车价格规则](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [优惠券代码](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [云基础架构上的Adobe Commerce：存储配置的最佳实践](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
