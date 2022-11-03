---
title: Adobe Commerce 2.3.5升级MariaDB先决条件
description: 了解如何准备Adobe Commerce数据库以从Adobe Commerce 2.3.5升级。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Adobe Commerce 2.3.5升级先决条件

本文介绍在从版本2.3.4或更低版本升级到Adobe Commerce 2.3.5时，如何准备数据库。

此升级要求支持团队将云基础架构上的MariaDB从MariaDB 10.0升级到10.2，以满足Adobe Commerce的要求。 Adobe Commerce版本2.3.5及更高版本。

## 受影响的产品和版本

Adobe Commerce on cloud infrastructure，其中包含Adobe Commerce版本2.3.4或更低版本以及MariaDB版本10.0或更低版本。

## 准备数据库以进行升级

在Adobe Commerce支持团队开始升级过程之前，必须通过转换 `COMPACT` to `DYNAMIC`. 您还必须从 `MyISAM` to `InnoDB`.

在创建计划并计划转换数据库时，请牢记以下准则。

- 从 `COMPACT` to `DYNAMIC` 使用大型数据库时，表格可能需要数小时。

- 要防止数据损坏，请勿在您的网站上线时执行转换。

- 在网站的低流量时段内完成转化工作。

- 将您的网站切换到 [维护模式](../../../installation/tutorials/maintenance-mode.md) 运行之前 `ALTER` 中。

### 转换数据库表

您可以转换群集中一个节点上的表。 这些更改将复制到群集中的其他核心节点。

1. 从云基础架构环境上的Adobe Commerce中，使用SSH连接到节点1。

1. 登录到MariaDB。

1. 转换表格式。

   - 识别要从压缩格式转换为动态格式的表。

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - 确定表大小，以便您可以计划转换工作。

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      要转换较大的表，需要较长的时间。 在进入和退出维护模式时，您应相应地规划要按顺序转换哪些批表，以便规划所需维护时段的时间

   - 将所有表一次转换为一个动态格式。

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. 更新表存储引擎。

   - 识别使用 `MyISAM` 存储。

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - 转换使用 `MyISAM` 存储到 `InnoDB` 存储。

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. 验证转换。

   此步骤是必需的，因为完成转换后进行的代码部署可能会导致某些表恢复为其原始配置。

   - 在计划升级到MariaDB版本10.2的前一天，登录数据库并运行查询以检查格式和存储引擎。

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - 如果任何表已还原，请重复这些步骤以更改表格式和存储引擎。

## 其他信息

[云基础架构上的Adobe Commerce数据库最佳实践](../planning/database-on-cloud.md)
