---
title: Adobe Commerce 2.3.5升级MariaDB先决条件
description: 了解如何准备Adobe Commerce数据库以从Adobe Commerce 2.3.5升级。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: bc38dd658401d3cd4c64159b1b2b2efe89979a93
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---


# MariaDB升级先决条件

从Adobe Commerce 2.3.4或更低版本升级到任何较新版本时，需要将云基础架构上的MariaDB服务从版本10.0或10.2升级到版本10.3或10.4。MariaDB版本10.3及更高版本要求数据库使用动态表行格式，而Adobe Commerce要求使用表的InnoDB存储引擎。 本文介绍如何更新数据库以符合这些MariaDB要求。

在准备数据库后，请提交Adobe Commerce支持票证，以更新云基础架构上的MariaDB服务版本，然后再继续执行Adobe Commerce升级过程。

## 受影响的产品和版本

Adobe Commerce on cloud infrastructure，其中包含Adobe Commerce版本2.3.4或更低版本以及MariaDB版本10.0或更低版本。

## 准备数据库以进行升级

在Adobe Commerce支持团队开始升级过程之前，请通过转换数据库表来准备数据库：

- 从 `COMPACT` to `DYNAMIC`
- 将存储引擎从 `MyISAM` to `InnoDB`

在规划和计划转化时，请牢记以下注意事项：

- 从 `COMPACT` to `DYNAMIC` 使用大型数据库时，表格可能需要数小时。

- 要防止数据损坏，请不要在实时网站上完成转换工作。

- 在网站的低流量时段内完成转化工作。

- 将您的网站切换到 [维护模式](../../../installation/tutorials/maintenance-mode.md) 运行转换数据库表的命令之前。

### 转换数据库表行格式

您可以转换群集中一个节点上的表。 更改会自动复制到其他服务节点。

1. 从云基础架构环境上的Adobe Commerce中，使用SSH连接到节点1。

1. 登录到MariaDB。

1. 识别要从压缩格式转换为动态格式的表。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 确定表大小，以便您可以计划转换工作。

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   要转换较大的表，需要较长的时间。 按优先级和表大小查看表并批量处理转换工作，以帮助规划所需的维护窗口。

1. 将所有表一次转换为一个动态格式。

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

### 转换数据库表存储格式

您可以转换群集中一个节点上的表。 更改会自动复制到其他服务节点。

对于Adobe Commerce Starter和Adobe Commerce Pro项目，转换存储格式的过程有所不同。

- 对于Starter体系结构，请使用MySQL `ALTER` 命令来转换格式。
- 在Pro架构上，使用MySQL `CREATE` 和 `SELECT` 用于创建数据库表的命令 `InnoDB` 将现有表中的数据存储并复制到新表中。 此方法可确保将更改复制到群集中的所有节点。

**转换Adobe Commerce Pro项目的表存储格式**

1. 识别使用 `MyISAM` 存储。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 将所有表转换为 `InnoDB` 存储格式。

   - 重命名现有表以防止名称冲突。

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - 创建使用 `InnoDB` 存储。

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - 验证新表包含所有必需数据。

   - 删除您重命名的原始表。


**转换Adobe Commerce入门项目的表存储格式**

1. 识别使用 `MyISAM` 存储。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 转换使用 `MyISAM` 存储到 `InnoDB` 存储。

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### 验证数据库转换

在计划升级到MariaDB版本10.2的前一天，请验证所有表都具有正确的行格式和存储引擎。 需要验证，因为完成转换后进行的代码部署可能会导致某些表还原到其原始配置。

1. 登录数据库。

1. 检查是否有 `COMPACT` 行格式。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 检查是否有任何仍使用 `MyISAM` 存储格式

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 如果有任何表已还原，请重复这些步骤以更改表行格式和存储引擎。

## 更改存储引擎

请参阅 [将MyISAM表转换为InnoDB](../planning/database-on-cloud.md).

## 其他信息

- [云基础架构上的Adobe Commerce数据库最佳实践](../planning/database-on-cloud.md)
- [在云上将适用于Adobe Commerce的MariaDB从10.0更新为12.0](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10.0-to-10.2-for-magento-commerce-cloud.html)

