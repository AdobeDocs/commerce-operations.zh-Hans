---
title: 更改增量ID
description: 更改商务数据库实体的增量ID。
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---


# 更改增量ID

本文讨论如何使用 `ALTER TABLE` SQL语句。

## 受影响的版本

- Adobe Commerce（内部）：2.x.x
- Adobe Commerce云基础架构：2.x.x
- MySQL: [任何受支持的版本]

## 您何时需要更改增量ID

在以下情况下，您可能需要更改新数据库实体的增量ID:

- 在实时网站上执行硬备份还原后
- 某些订单记录已丢失，但其ID已被支付网关（如PayPal）用于您当前的Merchant帐户。 在这种情况下，支付网关停止处理具有相同ID的新订单，返回“重复发票ID”错误

>[!INFO]
>
>您还可以通过在PayPal的“付款接收首选项”中允许每个发票ID进行多次付款来修复PayPal的付款网关问题。 请参阅 [PayPal网关拒绝请求 — 发票重复问题] 在 _知识库_.

## 先决条件步骤

1. 查找应更改新增量ID的商店和实体。
1. 连接到MySQL数据库。
对于云基础架构上的Adobe Commerce，您首先需要使用SSH连接到环境。
1. 检查当前 `auto_increment` 实体序列表的值：

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

如果要检查ID=1的存储上的订单的自动增量，则表名称将为“sequence_order_1”。

如果 `auto_increment` 列为“1234”，下一个订单是 `ID=1` 将具有ID &#39;#100001234&#39;。

## 更新实体以更改增量ID

使用以下查询更新实体：

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
重要信息：新增量值必须大于当前增量值。

执行以下查询后：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

下一份下一份订单 `ID=1` 将具有ID &#39;#100002000&#39;。

## 关于云生产环境的其他建议步骤

执行 `ALTER TABLE` 查询云基础架构上的Adobe Commerce生产环境，我们强烈建议执行以下步骤：

- 在暂存环境中测试更改增量ID的整个过程
- [创建数据库备份] 在出现故障时恢复生产数据库

<!-- Link Definitions -->

[PayPal网关拒绝请求 — 发票重复问题]: https://support.magento.com/hc/en-us/articles/115002457473
[创建数据库备份]: https://support.magento.com/hc/en-us/articles/360003254334
[任何受支持的版本]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html
