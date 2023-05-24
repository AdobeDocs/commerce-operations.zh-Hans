---
title: Adobe Commerce 2.3.5 MariaDB升级先决条件
description: 了解如何准备Adobe Commerce数据库以从Adobe Commerce 2.3.5升级。
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---

# 升级MariaDB的先决条件

从Adobe Commerce 2.3.4或更早版本升级到任何更新版本要求将云基础架构上的MariaDB服务从版本10.0或10.2升级到版本10.3或10.4。MariaDB版本10.3及更高版本要求数据库使用动态表行格式，而Adobe Commerce要求为表使用InnoDB存储引擎。 本文介绍如何更新数据库以符合这些MariaDB要求。

准备数据库后，请提交Adobe Commerce支持工单以更新云基础架构上的MariaDB服务版本，然后再继续Adobe Commerce升级过程。

## 受影响的产品和版本

使用Adobe Commerce版本2.3.4或更早版本以及MariaDB版本10.0或更早版本在云基础架构上部署Adobe Commerce。

## 准备数据库以进行升级

在Adobe Commerce支持团队开始升级过程之前，请通过转换数据库表来准备数据库：

- 转换行格式 `COMPACT` 到 `DYNAMIC`
- 更改存储引擎 `MyISAM` 到 `InnoDB`

在计划和计划转换时，请牢记以下注意事项：

- 转换自 `COMPACT` 到 `DYNAMIC` 使用大型数据库时，表可能需要几个小时。

- 为防止数据损坏，请勿在实时网站上完成转换工作。

- 在网站上的低流量期间完成转化工作。

- 将您的站点切换到 [维护模式](../../../installation/tutorials/maintenance-mode.md) 运行命令转换数据库表之前。

### 转换数据库表行格式

您可以在群集中的一个节点上转换表。 更改会自动复制到其他服务节点。

1. 在云基础架构环境上的Adobe Commerce中，使用SSH连接到节点1。

1. 登录MariaDB。

1. 标识要从压缩格式转换为动态格式的表。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 确定表大小，以便您可以安排转换工作。

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   较大的表需要较长时间才能转换。 查看表并按优先级和表大小对转换工作进行批处理，以帮助计划所需的维护窗口。

1. 将所有表逐个转换为动态格式。

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

### 转换数据库表存储格式

您可以在群集中的一个节点上转换表。 更改会自动复制到其他服务节点。

对于Adobe Commerce Starter和Adobe Commerce Pro项目，存储格式的转换过程不同。

- 对于入门体系结构，请使用MySQL `ALTER` 命令转换格式。
- 在Pro体系结构上，使用MySQL `CREATE` 和 `SELECT` 用于创建数据库表的命令 `InnoDB` 存储数据并将现有表中的数据复制到新表中。 此方法可确保将更改复制到群集中的所有节点。

**转换Adobe Commerce Pro项目的表存储格式**

1. 标识使用的表 `MyISAM` 存储。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 将所有表转换为 `InnoDB` 存储格式，一次一个。

   - 重命名现有表以防止名称冲突。

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - 创建使用 `InnoDB` 使用现有表中的数据进行存储。

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - 验证新表是否具有所有必需的数据。

   - 删除重命名的原始表。


**为Adobe Commerce Starter项目转换表存储格式**

1. 标识使用的表 `MyISAM` 存储。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 转换使用的表 `MyISAM` 存储到 `InnoDB` 存储。

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### 验证数据库转换

在计划升级到MariaDB版本10.2的前一天，请确认所有表都具有正确的行格式和存储引擎。 需要进行验证，因为完成转换后进行的代码部署可能会导致某些表还原为其原始配置。

1. 登录到数据库。

1. 检查任何仍具有 `COMPACT` 行格式。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 检查任何仍使用 `MyISAM` 存储格式

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 如果有任何表已还原，请重复这些步骤以更改表行格式和存储引擎。

## 更改存储引擎

参见 [将MyISAM表转换为InnoDB](../planning/database-on-cloud.md).

## 其他信息

- [云基础架构上Adobe Commerce的数据库最佳实践](../planning/database-on-cloud.md)
- [将Adobe Commerce on Cloud的MariaDB从10.0更新到12.0](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10.0-to-10.2-for-magento-commerce-cloud.html)
