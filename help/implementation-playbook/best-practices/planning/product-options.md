---
title: 产品选项配置最佳实践
description: 通过限制产品选项的数量来优化Adobe Commerce性能。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# 产品选项最佳实践

为获得最佳性能，每个产品最多配置100个产品选项。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 减少产品选项

为获得最佳网站性能，请使用以下策略来减少产品选项的数量：

- 将复杂产品和自定义选项配置为产品变体的来源。
- 使用属性集来构建具有目标属性和选项的特定产品模板，而不是创建应用于所有产品的全局产品模板和选项容器。
- 通过外部产品管理系统(PMS)管理产品信息。

## 潜在的性能影响

配置许多产品选项会增加在所有读写操作中检索到的每个产品的数据量，从而：

- 增加的SQL查询流量和更重的 `JOIN` 操作会提高数据库吞吐量。
- 增加了Adobe Commerce索引和全文搜索索引的大小。

上面列出的增加可能会通过以下方式影响网站性能：

- 与属性中包含许多选项的产品相关的大多数店面方案的响应时间会延长。
- 在管理员中完成产品管理操作所需的时间会显着增加，这可能会导致超时，特别是对于与属性列表和树检索相关的方案（包括促销规则管理），更是如此。
- 可以阻止完成异步批量操作的批量操作，例如导入和导出，以及将自定义价格分配给共享目录中的多个产品。

## 其他信息

- [创建产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [产品属性配置的最佳实践](product-attributes-and-options.md)
- [批量操作日志](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [库存批量操作API](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [培训：使用Adobe Commerce管理目录和产品](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)

