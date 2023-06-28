---
title: 产品选项配置最佳实践
description: 通过限制产品选项的数量来优化Adobe Commerce性能。
role: Admin
feature: Best Practices, Catalogs
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 产品选项最佳实践

为获得最佳性能，每个产品最多可配置100个产品选项。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 减少产品选项

为获得最佳站点性能，请使用以下策略来减少产品选项的数量：

- 配置复杂产品和自定义选项作为产品变体的来源。
- 使用属性集构建具有目标属性和选项的特定产品模板，而不是创建适用于所有产品的全局产品模板和选项容器。
- 通过外部产品管理系统(PMS)管理产品信息。

## 潜在的性能影响

配置多个产品选项会增加所有读取和写入操作中为每个产品检索的数据量，从而导致：

- 增加了SQL查询流量和更重 `JOIN` 操作提高了数据库吞吐量。
- 增加了Adobe Commerce索引和全文搜索索引的大小。

上面列出的增加可能会以下列方式影响站点性能：

- 与属性中包含许多选项的产品相关的大多数店面方案的响应时间更长。
- 显着增加了在“管理员”中完成产品管理操作所需的时间，这可能会导致超时，尤其是对于与属性列表和树检索（包括升级规则管理）相关的方案。
- 可以阻止完成异步批量操作的批量操作，例如导入和导出以及将自定义价格分配给共享目录中的多个产品。

## 其他信息

- [创建产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [产品属性配置的最佳实践](product-attributes-and-options.md)
- [批量操作日志](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [库存成批活动API](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [培训：使用Adobe Commerce管理目录和产品](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
