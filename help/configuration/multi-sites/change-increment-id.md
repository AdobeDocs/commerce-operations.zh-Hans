---
title: 更改增量ID
description: 更改Commerce数据库实体的增量ID。
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# 更改增量ID

本文讨论如何使用`ALTER TABLE` SQL语句更改特定Commerce存储中Commerce数据库(DB)实体（订单、发票、贷项通知单等）的增量ID。

## 受影响的版本

- Adobe Commerce（内部部署）：2.x.x
- 云基础架构上的Adobe Commerce：2.x.x
- MySQL： [任何支持的版本](../../installation/prerequisites/database/mysql.md)

## 何时需要更改增量ID

在以下情况下，您可能需要更改新数据库实体的增量ID：

- 在Live站点上进行硬备份还原之后
- 某些订单记录已丢失，但支付网关（如PayPal）已使用其ID作为您的当前商家帐户。 在这种情况下，付款网关将停止处理具有相同ID的新订单，并返回“重复发票ID”错误

>[!INFO]
>
>您还可以通过在PayPal的“付款接收首选项”中允许每个发票ID多次付款，修复PayPal的付款网关问题。 查看[PayPal网关拒绝的请求 — ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html?lang=zh-Hans)知识库&#x200B;_中的重复发票问题_。

## 必备步骤

1. 查找应更改新增量ID的存储和实体。
1. 连接到MySQL数据库。
对于云基础架构上的Adobe Commerce，您首先需要使用SSH连接到环境。
1. 使用以下查询检查实体序列表的当前`auto_increment`值：

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

如果要检查ID=1的商店中订单的自动递增，则表名称为“sequence_order_1”。

如果`auto_increment`列的值为“1234”，则使用`ID=1`在商店下单的订单的ID将为“#100001234”。

## 更新实体以更改增量ID

使用以下查询更新实体：

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>重要信息：新增量值必须大于当前增量值。

执行以下查询后：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

使用`ID=1`在商店下单的ID为“#100002000”。

## 关于云生产环境的其他建议步骤

在云基础架构上的Adobe Commerce的生产环境中执行`ALTER TABLE`查询之前，我们强烈建议执行以下步骤：

- 测试在暂存环境中更改增量ID的整个过程
- [创建数据库备份]以在失败时还原您的生产数据库

<!-- Link Definitions -->

[PayPal gateway rejected request - duplicate invoice issue]: https://support.magento.com/hc/en-us/articles/115002457473
[创建数据库备份]: https://support.magento.com/hc/en-us/articles/360003254334
[任何支持的版本]
