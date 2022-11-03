---
title: 产品变量配置最佳实践
description: 了解如何通过限制已配置的产品变体的数量来优化Adobe Commerce性能。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# 配置产品变体的最佳实践

为获得最佳性能，每个产品最多配置50个变体。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 减少产品变体的数量

为获得最佳网站性能，请使用以下策略来减少产品变体的数量：

- 通过在不同产品中分发变体数量来调整目录。
- 删除非库存的可配置属性选项。
- 通过自定义选项、类别、相关、分组和捆绑产品等替代功能管理变体。

## 潜在的性能影响

如果超出建议的产品变体数量，可能会通过以下方式影响网站性能：

- 包含复杂产品的产品详细信息和类别页面上的请求和渲染时间较长。
- 缩短了在管理员中完成保存操作的响应时间。
- 增加了渲染产品编辑表单的时间。
- 结帐缓慢。

## 其他信息

- [创建可配置产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [创建产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- 培训 — [使用Adobe Commerce管理目录和产品](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
