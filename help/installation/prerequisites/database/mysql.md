---
title: MySQL准则
description: 按照以下步骤安装和配置MySQL和MariaDB，以在本地安装Adobe Commerce和Magento Open Source。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# MySQL一般准则

请参阅 [系统要求](../../system-requirements.md) 的受支持版本。

Adobe _强烈_ 建议在设置数据库时遵守以下标准：

* Adobe Commerce和Magento Open Source使用 [MySQL数据库触发器](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) 以在重新索引期间改进数据库访问。 将索引器模式设置为 [计划](../../../configuration/cli/manage-indexers.md#configure-indexers). 该应用程序不支持数据库中的任何自定义触发器，因为自定义触发器可能会引入与未来Adobe Commerce和Magento Open Source版本的不兼容性。
* 熟悉 [这些潜在的MySQL触发器限制](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) 之前。
* 要增强数据库安全态势，请启用 [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL模式，以防止存储无效的数据值，这可能导致不需要的数据库交互。
* Adobe Commerce和Magento Open Sourcedo _not_ 支持基于MySQL语句的复制。 确保使用 _仅_ [基于行的复制](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce和Magento Open Source当前使用 `CREATE TEMPORARY TABLE` 交易内的报表， [不兼容](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) 对于数据库实施，使用基于GTID的复制，例如 [Google Cloud SQL第二代实例](https://cloud.google.com/sql/docs/features#differences). 将MySQL for Cloud SQL 8.0视为替代方法。

>[!NOTE]
>
>如果您的Web服务器和数据库服务器位于不同的主机上，请在数据库服务器主机上执行本主题中讨论的任务，然后参阅 [设置远程MySQL数据库连接](mysql-remote.md).

## 在Ubuntu上安装MySQL

Adobe Commerce和Magento Open Source2.4需要MySQL 8.0的全新安装。请按照以下链接，获取有关在计算机上安装MySQL的说明。

* [乌本图](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

如果您希望导入大量产品，则可以将 [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) 大于默认的16 MB。

>[!NOTE]
>
>默认值适用于云基础架构上的Adobe Commerce _和_ 内部项目。 Adobe Commerce on cloud infrastructure Pro客户必须开具支持票证以增加 `max_allowed_packet` 值。 Adobe Commerce on cloud infrastructure Starter客户可以通过更新 `/etc/mysql/mysql.cnf` 文件。

要增加值，请打开 `/etc/mysql/mysql.cnf` 文件，并找到 `max_allowed_packet`. 保存对 `mysql.cnf` 文件，关闭文本编辑器，然后重新启动MySQL(`service mysql restart`)。

要（可选）验证您设置的值，请在 `mysql>` 提示：

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

然后， [配置数据库实例](#configuring-the-database-instance).

## MySQL 8更改

对于Adobe Commerce和Magento Open Source2.4，我们添加了对MySQL 8的支持。
本节介绍开发人员应注意的对MySQL 8的主要更改。

### 删除了整数类型（内边距）的宽度

MySQL 8.0.17中已弃用整数数据类型(TINYINT、SMALLINT、MEDIAMINT、INT、BIGINT)的显示宽度规范。在其输出中包含数据类型定义的语句不再显示整数类型的显示宽度，TINYINT(1)除外。 MySQL连接器假定TINYINT(1)列源于BOOLEAN列。 这种例外使他们能够继续作出这种假设。

#### 示例

在mysql 8.19中描述admin_user

| 字段 | 类型 | Null | 键 | 默认 | 额外 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | 否 | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | 是 |  | `NULL` |  |
| `lastname` | `varchar(32`) | 是 |  | `NULL` |  |
| `email` | `varchar(128)` | 是 |  | `NULL` |  |
| `username` | `varchar(40)` | 是 | UNI | `NULL` |  |
| `password` | `varchar(255)` | 否 |  | `NULL` |  |
| `created` | `timestamp` | 否 |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | 否 |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` 更新 `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | 是 |  | `NULL` |  |
| `lognum` | `smallint unsigned` | 否 |  | `0` |  |

除 _TINYINT(1)_，应从 `db_schema.xml` 文件。

有关更多信息，请参阅 [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### 默认顺序（按行为）

在8.0之前，条目按外键排序。 默认排序顺序取决于所使用的引擎。
如果您的代码依赖于特定的排序，请始终指定排序顺序。

### 已弃用的ASC和DESC限定符，用于组依据

自MySQL 8.0.13起，已弃用 `ASC` 或 `DESC` 限定符 `GROUP BY` 子句已被删除。 以前依赖的查询 `GROUP BY` 排序可能会产生与以前的MySQL版本不同的结果。 要生成给定的排序顺序，请提供 `ORDER BY` 子句。

## Commerce和MySQL 8

对Adobe Commerce和Magento Open Source进行了一些更改，以正确支持MySQL 8。

### 查询和插入行为

Adobe Commerce和Magento Open Source通过在 `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. 禁用验证后，MySQL可能会截断数据。 在MySQL中，查询行为已发生更改： `Select * on my_table where IP='127.0.0.1'` 不再返回结果，因为IP地址现在被正确视为字符串，而不是整数。

## 从MySQL 5.7升级到MySQL 8

要将MySQL从版本5.7正确更新到版本8，您必须按顺序执行以下步骤：

1. 将Adobe Commerce或Magento Open Source升级到2.4.0。测试所有内容并确保系统按预期运行。
1. 启用维护模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 进行数据库备份：

   ```bash
   bin/magento setup:backup --db
   ```

1. 将MySQL更新到版本8。
1. 将备份数据导入MySQL。
1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```

1. 禁用维护模式：

   ```bash
   bin/magento maintenance:disable
   ```

## 配置数据库实例

本节讨论如何为Adobe Commerce或Magento Open Source创建数据库实例。 尽管建议使用新的数据库实例，但您可以选择安装Adobe Commerce或使用现有数据库实例进行Magento Open Source。

要配置MySQL数据库实例，请执行以下操作：

1. 以任何用户身份登录数据库服务器。
1. 转到MySQL命令提示符：

   ```bash
   mysql -u root -p
   ```

1. 输入MySQL `root` 用户的密码。
1. 按照创建名为的数据库实例的顺序输入以下命令 `magento` 带用户名 `magento`:

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

   如果显示MySQL监视器，则表示您已正确创建了数据库。 如果显示错误，请重复上述命令。

1. 如果您的Web服务器和数据库服务器位于不同的主机上，请在数据库服务器主机上执行本主题中讨论的任务，然后参阅 [设置远程MySQL数据库连接](mysql-remote.md).

   我们建议您根据业务需要配置数据库实例。 在配置数据库时，请牢记以下几点：

   * 索引器要求更高 `tmp_table_size` 和 `max_heap_table_size` 值（例如，64 M）。 如果您配置 `batch_size` 参数时，可以随表大小设置调整该值，以提高索引器性能。 请参阅 [优化指南](../../../performance/configuration.md) 以了解更多信息。

   * 为了获得最佳性能，请确保所有MySQL和Adobe Commerce或Magento Open Source索引表都可以保留在内存中(例如，配置 `innodb_buffer_pool_size`)。

   * 与其他MariaDB或MySQL版本相比，在MariaDB 10.4上重新建立索引需要更多时间。 请参阅 [配置最佳实践](../../../performance/configuration.md#indexers).

1. 对于MySQL `TIMESTAMP` 要遵循应用程序声明性架构（系统变量）所预期的首选项和组合的字段 `explicit_defaults_for_timestamp` 必须设置为 `on`.

   引用：

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   如果未启用此设置， `bin/magento setup:db:status` 总是报告 `Declarative Schema is not up to date`.

>[!NOTE]
>
>的 `explicit_defaults_for_timestamp` 设置已弃用。 此设置控制将在未来MySQL版本中删除的已弃用的TIMESTAMP行为。 删除这些行为后， `explicit_defaults_for_timestamp` 设置也会被删除。

>[!WARNING]
>
>对于云基础架构项目上的Adobe Commerce, `explicit_defaults_for_timestamp` MySQL(MariaDB)的设置默认为 _关闭_.

与其他MariaDB或MySQL版本相比，在MariaDB 10.4上重新建立索引需要更多时间。 要加快重新索引的速度，我们建议设置以下MariaDB配置参数：

* optimizer_switch=&#39;rowid_filter=off&#39;
* optimizer_use_condition_asepticity = 1
