---
title: 验证拆分数据库
description: 了解如何验证Commerce Split数据库配置是否正常工作。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# 验证拆分数据库

{{ee-only}}

{{deprecate-split-db}}

配置后，主控数据库的配置如下所示：

- 主商务数据库：369个表
- 商务报价数据库：11个表
- 商务销售数据库：55个表

要验证拆分数据库是否正常工作，请执行以下任务，并使用数据库工具(如 [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| 验证内容 | 如何验证 |
| -------------- | ------------- |
| 报价数据库正在工作 | 将项目添加到购物车。 验证行是否已添加到报价数据库的 `quote`, `quote_address`和 `quote_item` 表格。 |
| 销售数据库正在工作 | 完成订单（任何付款方式，包括支票/货币订单）。 验证行是否已添加到您销售数据库的 `sales_order_address`, `sales_order_item`和 `sales_order_payment` 表格。 |

>[!WARNING]
>
>您必须手动备份另外两个数据库实例。 商务仅备份主数据库实例。 的 [`magento setup:backup --db`](../../installation/tutorials/backup.md) 命令和管理选项不备份其他表。
