---
title: MySQL准则
description: 按照以下步骤为Adobe Commerce的内部安装安装和配置MySQL和MariaDB。
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# 一般MySQL准则

有关支持的MySQL版本，请参阅[系统要求](../../system-requirements.md)。

Adobe _强烈_&#x200B;建议您在设置数据库时遵循以下标准：

* Adobe Commerce使用[MySQL数据库触发器](https://dev.mysql.com/doc/refman/8.0/en/triggers.html)来改进重新索引期间的数据库访问。 当索引器模式设置为[计划](../../../configuration/cli/manage-indexers.md#configure-indexers)时，将创建这些项。 应用程序不支持数据库中的任何自定义触发器，因为自定义触发器可能会与将来的Adobe Commerce版本不兼容。
* 在继续之前，请熟悉[这些潜在的MySQL触发器限制](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html)。
* 要增强数据库的安全状态，请启用[`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL模式以防止存储无效的数据值，这可能会导致不必要的数据库交互。
* Adobe Commerce _不_&#x200B;支持基于MySQL语句的复制。 确保仅使用&#x200B;_1&rbrace;_&#x200B;基于行的复制[。](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html)

>[!WARNING]
>
>Adobe Commerce当前在事务中使用`CREATE TEMPORARY TABLE`语句，这些语句与数据库实现中的[不兼容](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html)使用基于GTID的复制，如[Google Cloud SQL第二代实例](https://cloud.google.com/sql/docs/features#differences)。 考虑使用MySQL for Cloud SQL 8.0作为替代方法。

>[!NOTE]
>
>如果Web服务器和数据库服务器位于不同的主机上，请在数据库服务器主机上执行本主题中讨论的任务，然后参阅[设置远程MySQL数据库连接](mysql-remote.md)。

## 在Ubuntu上安装MySQL

Adobe Commerce 2.4要求全新安装MySQL 8.0。有关在计算机上安装MySQL的说明，请按照下面的链接操作。

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

如果您希望导入大量产品，可以将[`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html)的值增加到大于默认值16 MB的值。

>[!NOTE]
>
>默认值适用于云基础架构&#x200B;_和_&#x200B;内部部署项目上的Adobe Commerce。 云基础架构上的Adobe Commerce Pro客户必须打开支持工单才能增加`max_allowed_packet`值。 云基础架构上的Adobe Commerce入门客户可以通过更新`/etc/mysql/mysql.cnf`文件中的配置来增加值。

若要增加值，请在文本编辑器中打开`/etc/mysql/mysql.cnf`文件，然后找到`max_allowed_packet`的值。 保存对`mysql.cnf`文件所做的更改，关闭文本编辑器，然后重新启动MySQL (`service mysql restart`)。

要选择性地验证您设置的值，请在`mysql>`提示符下输入以下命令：

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

然后，[配置数据库实例](#configuring-the-database-instance)。

## MySQL 8更改

对于Adobe Commerce 2.4，我们添加了对MySQL 8的支持。
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
| `modified` | `timestamp` | 否 | | `CURRENT_TIMESTAMP` | 更新`DEFAULT_GENERATED`时`CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | 是 | | `NULL` | |
| `lognum` | `smallint unsigned` | 否 | | `0` | |

除&#x200B;_TINYINT(1)_&#x200B;外，应从`db_schema.xml`文件中删除所有整数填充(TINYINT > 1、SMALLINT、MEDIUMINT、INT、BIGINT)。

有关详细信息，请参阅[https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature)。

### 默认ORDER BY行为

在8.0之前，条目按外键排序。 默认排序顺序取决于使用的引擎。
如果您的代码依赖于特定排序，请始终指定排序顺序。

### GROUP BY的已弃用ASC和DESC限定符

自MySQL 8.0.13起，已删除`ASC`子句的已弃用`DESC`或`GROUP BY`限定符。 以前依赖于`GROUP BY`排序的查询可能会产生与以前的MySQL版本不同的结果。 要生成给定的排序顺序，请提供`ORDER BY`子句。

## Commerce和MySQL 8

为了正确支持MySQL 8，对Adobe Commerce进行了一些更改。

### 查询和插入行为

Adobe Commerce通过在`/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`中设置SET SQL_MODE=&quot;来禁用常规验证行为。 禁用验证后，MySQL可能会截断数据。 在MySQL中，查询行为已更改： `Select * on my_table where IP='127.0.0.1'`不再返回结果，因为IP地址现在被正确视为字符串而不是整数。

## 从MySQL 5.7升级到MySQL 8

要将MySQL从版本5.7正确更新到版本8，必须按照以下顺序执行以下步骤：

1. 将Adobe Commerce升级到2.4.0。
测试所有内容，并确保系统按预期工作。
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

本节讨论如何为Adobe Commerce创建数据库实例。 虽然建议使用新数据库实例，但您可以选择将Adobe Commerce与现有数据库实例一起安装。

配置MySQL数据库实例：

1. 以任意用户身份登录到数据库服务器。
1. 转到MySQL命令提示符：

   ```bash
   mysql -u root -p
   ```

1. 出现提示时输入MySQL `root`用户的密码。
1. 按照显示的顺序输入以下命令，以创建名为`magento`且用户名为`magento`的数据库实例：

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

1. 输入`exit`退出命令提示符。

1. 验证数据库：

   ```bash
   mysql -u magento -p
   ```

   如果显示MySQL监视器，则表示您正确创建了数据库。 如果显示错误，请重复上述命令。

1. 如果Web服务器和数据库服务器位于不同的主机上，请在数据库服务器主机上执行本主题中讨论的任务，然后参阅[设置远程MySQL数据库连接](mysql-remote.md)。

   我们建议您根据业务需要配置数据库实例。 在配置数据库时，请牢记以下几点：

   * 索引器需要更高的`tmp_table_size`和`max_heap_table_size`值（例如，64 M）。 如果配置`batch_size`参数，则可以调整该值以及表大小设置，以提高索引器性能。 有关详细信息，请参阅[优化指南](../../../performance/configuration.md)。

   * 为获得最佳性能，请确保所有MySQL和Adobe Commerce索引表都可以保留在内存中（例如，配置`innodb_buffer_pool_size`）。

   * 与其他MariaDB或MySQL版本相比，在MariaDB 10.4上重新索引需要更多时间。 请参阅[配置最佳实践](../../../performance/configuration.md#indexers)。

1. 要使MySQL `TIMESTAMP`字段遵循应用程序的声明性架构架构所预期的首选项和构成，系统变量`explicit_defaults_for_timestamp`必须设置为`on`。

   引用：

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   如果未启用此设置，`bin/magento setup:db:status`将始终报告`Declarative Schema is not up to date`。

>[!NOTE]
>
>`explicit_defaults_for_timestamp`设置已弃用。 此设置控制将在未来MySQL版本中删除的已弃用TIMESTAMP行为。 删除这些行为时，`explicit_defaults_for_timestamp`设置也会被删除。

>[!WARNING]
>
>对于云基础架构项目上的Adobe Commerce，MySQL (MariaDB)的`explicit_defaults_for_timestamp`设置默认为&#x200B;_OFF_。

{{$include /help/_includes/maria-db-config.md}}
