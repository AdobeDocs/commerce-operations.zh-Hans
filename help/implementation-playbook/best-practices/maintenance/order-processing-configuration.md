---
title: 订单处理的配置最佳实践
description: 了解配置最佳实践以提高结账和订单处理性能。
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# 订单处理的配置最佳实践

随着Commerce网站上订购量的增加，您可以通过启用以下商店配置选项来优化结账性能和订单处理：

- **[!UICONTROL Asynchronous indexing]** — 启用此选项可防止同时下达大量订单时数据库锁定并减慢处理速度。
- **[!UICONTROL Asynchronous email notifications]** — 启用此选项以按指定的间隔发送结帐和订单处理电子邮件通知而不是立即发送它们，从而加快结帐性能。
- **[!UICONTROL Enable Archiving]** — 启用此选项可提高订单、发票、装运和贷项通知单的性能，并使您的工作区不会出现不必要的信息，因此您可以专注于当前业务。 请参阅[启用存档](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving)。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 启用异步订单处理

启用异步订单处理的步骤取决于部署模式：

- 对于处于生产模式的云基础架构和本地站点上的Adobe Commerce，请使用以下MagentoCLI命令启用异步索引：

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- 对于处于默认或生产模式的Adobe Commerce本地站点，可通过在管理员中更新网格设置配置来启用异步索引。

  请参阅[启用计划的网格更新并重新索引](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >在更新生产环境之前，请始终在暂存环境中测试配置更改。

## 其他信息

- [配置最佳实践](../../../performance/configuration.md)
- [常规和高级配置路径参考](../../../configuration/reference/config-reference-general.md)
- [高吞吐量订单处理](../../../performance/high-throughput-order-processing.md)
