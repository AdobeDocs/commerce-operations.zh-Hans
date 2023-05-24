---
title: 类别配置最佳实践
description: 了解通过限制目录中的类别数量来最大化站点性能的最佳实践。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: c6834b32-9ee8-4a4a-932c-9726f3feee3f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 类别配置的最佳实践

为获得最佳性能，为Adobe Commerce站点配置的类别数量不要超过建议的最大数量。

- 对于Adobe Commerce版本2.4.2及更高版本，最多配置6000个类别
- 对于Adobe Commerce版本2.3.x和2.4.0到2.4.1-p1，请配置最多3000个类别

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 减少产品数量

使用以下策略来减少类别的数量：

- 通过属性和自定义选项管理独特的产品功能
- 删除不活动的类别
- 优化导航中的目录深度

## 潜在的性能影响

如果类别数量超过建议的最大数量，则可能会以下列方式影响站点性能：

- 显着提高了非缓存目录页面的响应时间
- 从管理员管理类别时的长时间执行和超时
- 增加相应数据库表的大小
- 较大的索引表会增加完成索引操作所需的时间 `[category/product relation index\]`
- 增加了完成类别树构建、菜单检索和类别规则管理操作的处理时间

## 其他信息

- [类别概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [导航概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [产品分配](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [云基础架构上的Adobe Commerce：存储配置的最佳实践](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
