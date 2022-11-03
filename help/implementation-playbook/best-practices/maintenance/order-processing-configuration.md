---
title: 订单处理的配置最佳实践
description: 了解配置最佳实践，以提高结帐和订单处理性能。
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# 订单处理的配置最佳实践

随着商务网站上的订单量增加，您可以通过启用以下商店配置选项来优化结帐性能和订单处理：

- **[!UICONTROL Asynchronous indexing]** — 启用此选项可防止在同时下达大量订单时出现数据库锁定和处理速度减慢的情况。
- **[!UICONTROL Asynchronous email notifications]** — 启用此选项，可通过以指定的间隔发送结帐和订单处理电子邮件通知，而不是立即发送，从而加快结帐性能。
- **[!UICONTROL Enable Archiving]** — 启用此选项可存档订单并释放数据库磁盘空间，以加快订单处理。 请参阅 [启用存档](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 启用异步订单处理

启用异步订单处理的步骤取决于部署模式：

- 对于在云基础架构上的Adobe Commerce以及在生产模式下的内部部署站点，请使用以下MagentoCLI命令启用异步索引：

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- 对于默认或生产模式下的Adobe Commerce本地站点，请通过更新“管理员”中的“网格设置”配置来启用异步索引。

   请参阅 [启用计划网格更新和重新索引](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >在更新生产环境之前，应始终在暂存环境中测试配置更改。

## 其他信息

- [配置最佳实践](../../../performance/configuration.md)
- [常规和高级配置路径参考](../../../configuration/reference/config-reference-general.md)
- [高吞吐量订单处理](../../../performance/high-throughput-order-processing.md)
