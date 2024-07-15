---
title: 验证拆分数据库
description: 了解如何验证Commerce拆分数据库配置是否正常工作。
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# 验证拆分数据库

{{ee-only}}

{{deprecate-split-db}}

配置后，master数据库的配置如下：

- Commerce主数据库：369个表
- Commerce报价数据库：11个表
- Commerce sales数据库：55个表

要验证拆分数据库是否正常工作，请使用数据库工具（如[phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin)）执行以下任务并验证是否将数据添加到数据库表中：

| 验证内容 | 如何验证 |
| -------------- | ------------- |
| 报价数据库正在工作 | 将项目添加到购物车。 验证是否已将行添加到报价数据库的`quote`、`quote_address`和`quote_item`表中。 |
| 销售数据库正在工作 | 完成订单（任何支付方式，包括支票/汇票）。 验证是否已将行添加到销售数据库的`sales_order_address`、`sales_order_item`和`sales_order_payment`表中。 |

>[!WARNING]
>
>必须手动备份另外两个数据库实例。 Commerce仅备份主数据库实例。 [`magento setup:backup --db`](../../installation/tutorials/backup.md)命令和Admin选项不备份其他表。
