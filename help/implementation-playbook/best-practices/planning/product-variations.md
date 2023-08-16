---
title: 产品变体配置最佳实践
description: 了解如何通过限制配置的产品变体的数量来优化Adobe Commerce性能。
role: Admin
feature: Best Practices, Catalogs
exl-id: a19dd8b4-23b8-498f-be51-a0adfcd12a11
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# 配置产品变体的最佳实践

为获得最佳性能，每个产品最多可配置50个变体。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 减少产品变体的数量

为获得最佳网站性能，请使用以下策略减少产品变体的数量：

- 通过分发不同产品的变体数量来重构目录。
- 删除没有库存的可配置属性选项。
- 通过自定义选项、类别、相关、分组和捆绑产品等替代功能管理变体。

## 潜在的性能影响

超出建议数量的产品变体可能会以下列方式影响网站性能：

- 产品详细信息和包含复杂产品的类别页面上的请求和渲染时间较长。
- 增加了在管理员中完成保存操作的响应时间。
- 增加了呈现产品编辑表单的时间。
- 结账缓慢。

## 其他信息

- [创建可配置产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [创建产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- 培训 — [使用Adobe Commerce管理目录和产品](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
