---
title: MySQL准则
description: 按照以下步骤安装和配置MySQL和MariaDB，以进行Adobe Commerce和Magento Open Source的内部安装。
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# 一般MySQL准则

请参阅 [系统要求](../../system-requirements.md) 支持的MySQL版本。

Adobe _强烈_ 建议您在设置数据库时遵循以下标准：

* Adobe Commerce和Magento Open Source使用 [MySQL数据库触发器](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) 改进重新索引期间的数据库访问。 当索引器模式设置为时，将创建这些项 [计划](../../../configuration/cli/manage-indexers.md#configure-indexers). 应用程序不支持数据库中的任何自定义触发器，因为自定义触发器可能会与将来的Adobe Commerce和Magento Open Source版本不兼容。
* 熟悉 [这些潜在的MySQL触发器限制](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) 然后再继续。
* 要增强数据库安全状态，请启用 [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL模式，用于防止存储无效的数据值，这可能会导致不需要的数据库交互。
* Adobe Commerce和Magento Open Source do _非_ 支持基于MySQL语句的复制。 确保使用 _仅限_ [基于行的复制](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce当前使用 `CREATE TEMPORARY TABLE` 事务中的语句，这些语句 [不兼容](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) 对于数据库实施，使用基于GTID的复制，例如 [Google Cloud SQL第二代实例](https://cloud.google.com/sql/docs/features#differences). 考虑使用MySQL for Cloud SQL 8.0作为替代方法。

>[!NOTE]
>
>如果Web服务器和数据库服务器位于不同的主机上，请在数据库服务器主机上执行本主题中讨论的任务，然后请参见 [设置远程MySQL数据库连接](mysql-remote.md).

## 在Ubuntu上安装MySQL

Adobe Commerce和Magento Open Source2.4需要全新安装MySQL 8.0。有关在计算机上安装MySQL的说明，请按照下面的链接操作。

* [乌班图](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

如果您预计会导入大量产品，则可以增加 [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) 大于默认值16 MB。

>[!NOTE]
>
>默认值适用于云基础架构上的Adobe Commerce _和_ 内部部署项目。 Adobe Commerce on cloud infrastructure Pro客户必须开立支持工单以增加 `max_allowed_packet` 值。 云基础架构上的Adobe Commerce入门客户可以通过更新 `/etc/mysql/mysql.cnf` 文件。

要增加值，请打开 `/etc/mysql/mysql.cnf` 在文本编辑器中查找的值 `max_allowed_packet`. 将更改保存到 `mysql.cnf` 文件，关闭文本编辑器，然后重新启动MySQL (`service mysql restart`)。

要验证设置的值（可选），请在 `mysql>` 提示：

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

然后， [配置数据库实例](#configuring-the-database-instance).

## MySQL 8更改

对于Adobe Commerce和Magento Open Source2.4，我们添加了对MySQL 8的支持。
本节介绍开发人员应了解的对MySQL 8的主要更改。

### 已移除整数类型的宽度（填充）

在MySQL 8.0.17中，已弃用整数数据类型(TINYINT、SMALLINT、MEDIUMINT、INT、BIGINT)的显示宽度规范。在输出中包含数据类型定义的语句不再显示整数类型的显示宽度，TINYINT(1)除外。 MySQL连接器假定TINYINT(1)列源自BOOLEAN列。 这一例外使他们能够继续作出这一假设。

#### 示例

在mysql 8.19中描述admin_user

| 字段 | 类型 | 空 | 键 | 默认 | 额外 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | 否 | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | 是 | | `NULL` | |
| `lastname` | `varchar(32`) | 是 | | `NULL` | |
| `email` | `varchar(128)` | 是 | | `NULL` | |
| `username` | `varchar(40)` | 是 | UNI | `NULL` | |
| `password` | `varchar(255)` | 否 | | `NULL` | |
| `created` | `timestamp` | 否 | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | 否 | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` 更新 `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | 是 | | `NULL` | |
| `lognum` | `smallint unsigned` | 否 | | `0` | |

除了 _TINYINT(1)_，所有整数边距(TINYINT > 1， SMALLINT， MEDIUMINT， INT， BIGINT)应从 `db_schema.xml` 文件。

有关更多信息，请参阅 [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### 默认ORDER BY行为

在8.0之前，条目按外键排序。 默认排序顺序取决于使用的引擎。
如果您的代码依赖于特定排序，请始终指定排序顺序。

### GROUP BY的已弃用ASC和DESC限定符

自MySQL 8.0.13起，已弃用 `ASC` 或 `DESC` 限定符 `GROUP BY` 已删除子句。 以前依赖的查询 `GROUP BY` 排序可能会产生与以前的MySQL版本不同的结果。 要生成给定的排序顺序，请提供 `ORDER BY` 子句。

## Commerce和MySQL 8

为了正确支持MySQL 8，对Adobe Commerce和Magento Open Source进行了一些更改。

### 查询和插入行为

Adobe Commerce和Magento Open Source通过在以下位置设置SET SQL_MODE=&quot;来禁用常规验证行为 `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. 禁用验证后，MySQL可能会截断数据。 在MySQL中，查询行为已更改： `Select * on my_table where IP='127.0.0.1'` 不再返回结果，因为IP地址现在正确显示为字符串而不是整数。

## 从MySQL 5.7升级到MySQL 8

要将MySQL从版本5.7正确更新到版本8，必须按照以下顺序执行以下步骤：

1. 将Adobe Commerce或Magento Open Source升级到2.4.0。测试所有内容，并确保系统按预期工作。
1. 启用维护模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 进行数据库备份：

   ```bash
   bin/magento setup:backup --db
   ```

1. 将MySQL更新到版本8。
1. 将备份的数据导入MySQL。
1. 清理缓存：

   ```bash
   bin/magento cache:clean
   ```

1. 禁用维护模式：

   ```bash
   bin/magento maintenance:disable
   ```

## 配置数据库实例

本节讨论如何为Adobe Commerce或Magento Open Source创建数据库实例。 尽管建议使用新数据库实例，但您可以选择安装Adobe Commerce或与现有数据库实例Magento Open Source。

配置MySQL数据库实例：

1. 以任意用户身份登录到数据库服务器。
1. 转到MySQL命令提示符：

   ```bash
   mysql -u root -p
   ```

1. 输入MySQL `root` 提示时用户的密码。
1. 按照显示的顺序输入以下命令，以创建名为的数据库实例 `magento` 使用用户名 `magento`：

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. 输入 `exit` 退出命令提示符。

1. 验证数据库：

   ```bash
   mysql -u magento -p
   ```

   如果显示MySQL监视器，则表示您正确创建了数据库。 如果显示错误，请重复上述命令。

1. 如果Web服务器和数据库服务器位于不同的主机上，请在数据库服务器主机上执行本主题中讨论的任务，然后请参见 [设置远程MySQL数据库连接](mysql-remote.md).

   我们建议您根据业务需要配置数据库实例。 在配置数据库时，请牢记以下几点：

   * 索引器的要求更高 `tmp_table_size` 和 `max_heap_table_size` 值（例如，64 M）。 如果您配置 `batch_size` 参数)时，可以调整该值以及表大小设置以提高索引器性能。 请参阅 [Optimization指南](../../../performance/configuration.md) 以了解更多信息。

   * 为获得最佳性能，请确保所有MySQL和Adobe Commerce或Magento Open Source索引表都可以保存在内存中(例如，配置 `innodb_buffer_pool_size`)。

   * 与其他MariaDB或MySQL版本相比，在MariaDB 10.4上重新索引需要更多时间。 请参阅 [配置最佳实践](../../../performance/configuration.md#indexers).

1. 用于MySQL `TIMESTAMP` 用于遵循应用程序的声明性架构架构（系统变量）所期望的首选项和组合的字段 `explicit_defaults_for_timestamp` 必须设置为 `on`.

   引用：

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   如果未启用此设置， `bin/magento setup:db:status` 始终报告 `Declarative Schema is not up to date`.

>[!NOTE]
>
>此 `explicit_defaults_for_timestamp` 设置已弃用。 此设置控制将在未来MySQL版本中删除的已弃用TIMESTAMP行为。 当这些行为被移除后， `explicit_defaults_for_timestamp` 设置也会被删除。

>[!WARNING]
>
>对于云基础架构项目上的Adobe Commerce， `explicit_defaults_for_timestamp` MySQL (MariaDB)的设置默认为 _关闭_.

{{$include /help/_includes/maria-db-config.md}}
