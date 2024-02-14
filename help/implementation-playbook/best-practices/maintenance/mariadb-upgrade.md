---
title: MariaDB的Adobe Commerce升级先决条件
description: 了解如何准备Adobe Commerce数据库以从以前的版本升级MariaDB。
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# 升级MariaDB的先决条件

在云基础架构上升级Adobe Commerce之前，如果您使用的是MariaDB，则还需要升级数据库软件。 例如：

- Adobe Commerce 2.4.6适用于MariaDB 10.5.1或更高版本
- Adobe Commerce 2.3.5与MariaDB版本10.3或更低版本

## Adobe Commerce 2.4.6

从MariaDB 10.5.1开始，使用旧临时格式的列使用 `/* mariadb-5.3 */` 注释在输出中 `SHOW CREATE TABLE`， `SHOW COLUMNS`， `DESCRIBE` 语句，以及 `COLUMN_TYPE` 列 `INFORMATION_SCHEMA.COLUMNS` 表格。 [请参阅MariaDB文档](https://mariadb.com/kb/en/datetime/#internal-format).

由于MariaDB注释，Adobe Commerce无法将日期列映射到正确的数据类型，这可能会导致自定义代码中出现意外行为。

为避免在将MariaDB从旧版本升级到版本10.6时出现意外行为，Adobe建议将列迁移到新的内部格式。

### 默认配置

在MariaDB 10.1.2中，从MySQL 5.6引入了一种新的临时格式。此 `mysql56_temporal_format` 系统变量允许数据库在执行alter表或导入数据库时自动将旧日期格式转换为新日期格式。 的默认配置 `mysql56_temporal_format` 在云基础架构上的Adobe Commerce上始终启用。

### 迁移日期列

以下查询显示将MariaDB升级到10.5.1或更高版本后必须迁移的受影响表和列：

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

将列迁移到新的内部日期格式需要重新导入数据库，或使用相同的列定义对标识的列执行更改。 以下查询生成必要的更改查询：

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>请务必将这些列迁移到新的内部日期格式 _早于_ 部署新代码以避免意外行为。

## Adobe Commerce 2.3.5

将云基础架构上的MariaDB服务从版本10.0或10.2升级到版本10.3、10.4或10.5。MariaDB版本10.3及更高版本要求数据库使用动态表行格式，而Adobe Commerce要求为表使用InnoDB存储引擎。 本文介绍如何更新数据库以符合这些MariaDB要求。

准备数据库后，请提交Adobe Commerce支持工单以更新云基础架构上的MariaDB服务版本，然后再继续Adobe Commerce升级过程。

### 准备数据库以进行升级

在Adobe Commerce支持团队开始升级过程之前，请通过转换数据库表准备数据库：

- 转换行格式 `COMPACT` 到 `DYNAMIC`
- 更改存储引擎 `MyISAM` 到 `InnoDB`

在计划和计划转换时，请牢记以下注意事项：

- 转换自 `COMPACT` 到 `DYNAMIC` 对于大型数据库，表可能需要几个小时。

- 为防止数据损坏，请勿在实时网站上完成转换工作。

- 在网站上的低流量期间完成转化工作。

- 将您的站点切换到 [维护模式](../../../installation/tutorials/maintenance-mode.md) 运行命令转换数据库表之前。

#### 转换数据库表行格式

您可以在群集中的一个节点上转换表。 更改会自动复制到其他服务节点。

1. 在云基础架构环境上的Adobe Commerce中，使用SSH连接到节点1。

1. 登录MariaDB。

1. 标识要从压缩格式转换为动态格式的表。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 确定表大小，以便您可以计划转换工作。

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   较大的表需要较长时间才能转换。 复查这些表并按优先级和表大小对转换工作进行批处理，以帮助计划所需的维护窗口。

1. 将所有表逐个转换为动态格式。

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### 转换数据库表存储格式

您可以在群集中的一个节点上转换表。 更改会自动复制到其他服务节点。

对于Adobe Commerce Starter和Adobe Commerce Pro项目，转换存储格式的过程不同。

- 对于入门体系结构，请使用MySQL `ALTER` 命令转换格式。
- 在Pro体系结构上，使用MySQL `CREATE` 和 `SELECT` 用于创建数据库表的命令 `InnoDB` 存储数据并将现有表中的数据复制到新表中。 此方法可确保将更改复制到群集中的所有节点。

**转换Adobe Commerce Pro项目的表存储格式**

1. 标识使用的表 `MyISAM` 存储。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 将所有表转换为 `InnoDB` 存储格式。

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

#### 验证数据库转换

在计划升级到MariaDB版本10.3、10.4或10.6的前一天，请确认所有表都具有正确的行格式和存储引擎。 需要进行验证，因为完成转换后进行的代码部署可能会导致某些表还原为其原始配置。

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

### 更改存储引擎

请参阅 [将MyISAM表转换为InnoDB](../planning/database-on-cloud.md).
