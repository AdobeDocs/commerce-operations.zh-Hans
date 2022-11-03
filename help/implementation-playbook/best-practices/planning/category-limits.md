---
title: 类别配置最佳实践
description: 了解最佳实践，通过限制目录中的类别数量来最大化网站性能。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# 类别配置的最佳实践

为获得最佳性能，请勿为Adobe Commerce网站配置超出最大建议类别数。

- 对于Adobe Commerce版本2.4.2及更高版本，最多配置6000个类别
- 对于Adobe Commerce版本2.3.x和2.4.0到2.4.1-p1，最多配置3000个类别

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 减少产品数量

使用以下策略减少类别数：

- 通过属性和自定义选项管理独特的产品功能
- 删除不活动的类别
- 在导航中优化目录深度

## 潜在的性能影响

超过建议的最大类别数可能会通过以下方式影响网站性能：

- 非缓存目录页面响应时间的显着增加
- 从管理员管理类别时执行时间过长和超时过长
- 相应数据库表的大小增加
- 较大的索引表可增加完成对 `[category/product relation index\]`
- 增加了处理时间，以完成类别树构建、菜单检索和类别规则管理操作

## 其他信息

- [类别概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [导航概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [产品分配](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce云基础架构：存储配置最佳实践](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
