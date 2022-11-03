---
title: 配置促销活动的最佳实践
description: 了解配置销售规则和优惠券代码以优化商务商店性能的最佳实践。
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# 配置促销活动的最佳实践

为获得最佳效果，请按照以下最佳实践为购物车中的项目配置销售和促销：

- **销售规则（购物车价格规则）** — 为所有网站配置不超过1000个购物车价格规则
   - 管理和删除未使用的规则。
   - 添加严格的规则条件（如属性或类别筛选器）以实现最有效的匹配。
- **优惠券**—
   - 验证数据库中的优惠券总数是否少于250,000。
   - 删除未使用和过期的优惠券。
   - 仅生成满足营销活动要求所需的优惠券数量。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 潜在的性能影响

超过建议的购物车价格规则或优惠券的最大数量可能会通过以下方式影响网站性能：

- 增加了将产品添加到购物车时的响应时间。
- 增加了加载和渲染小型机的时间。
- 增加了渲染购物车页面的时间。
- 增加了渲染 **总计** 块。
- 应用优惠券可能需要超过2秒。

## 其他信息

- [了解营销活动和促销活动](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [购物车价格规则](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [教程：创建购物车价格规则](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [优惠券代码](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce云基础架构：存储配置最佳实践](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
