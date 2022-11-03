---
title: 解决数据库性能问题的最佳实践
description: 了解如何修复导致在云基础架构上部署的Adobe Commerce站点上性能下降的数据库问题。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---


<!--Consider moving this topic to the Maintenance section-->

# 解决数据库性能问题的最佳实践

本文讨论如何修复对云基础架构站点上的Adobe Commerce数据库性能产生负面影响的数据库问题。

## 受影响的版本

Adobe Commerce云基础架构

## 识别并解决长时间运行的查询

确定MySQL查询是否运行缓慢。 根据您的Adobe Commerce云基础架构计划以及工具可用性，您可以执行以下操作。

### 使用MySQL分析数据库查询

您可以使用MySQL来识别和解决云基础架构项目上任何Adobe Commerce上长时间运行的查询。

1. 运行 [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) 语句。
1. 如果您看到运行时间较长的查询，请运行 [MySQL `EXPLAIN` 和 `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) 对于每个查询，要了解导致查询长时间运行的原因。
1. 根据发现的问题，采取步骤修复查询，以便更快地运行。

### 使用Percona Toolkit分析查询（仅适用于Pro架构）

如果您的Adobe Commerce项目是在Pro架构上部署的，则可以使用Percona Toolkit来分析查询。

1. 运行 `pt-query-digest --type=slowlog` 命令。
   * 要查找慢速查询日志的位置，请参阅 **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs)。
   * 请参阅 [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) 文档。
1. 根据发现的问题，采取步骤修复查询，以便更快地运行。

## 验证所有表都具有主键

定义主键是良好的数据库和表设计的要求。 主键提供了一种唯一标识任何表中单行的方法。

如果有没有主键的表，则Adobe Commerce(InnoDB)的默认数据库引擎将使用第一个唯一非空键作为主键。 如果没有唯一的密钥可用，InnoDB将创建一个隐藏的主密钥（6字节）。 隐式定义的主键的问题在于您无权控制它。 此外，对于没有主键的所有表，都会全局分配隐式值。 如果对这些表同时执行写入，此配置可能会导致争用问题。 这可能会导致性能问题，因为表还共享全局隐藏的主键索引增量。

通过为没有主键的表定义主键来防止这些问题。

### 识别和更新没有主键的表

1. 使用以下SQL查询标识没有主键的表：

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. 对于任何缺少主键的表，请通过更新 `db_schema.xml` （声明性模式），节点类似于以下内容：

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   添加节点时，请将 `referenceID` 和 `column name` 变量。

有关更多信息，请参阅 [配置声明性架构](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) ，请参阅我们的开发人员文档。

## 识别并删除重复的索引

识别数据库中的任何重复索引并删除它们。

### 检查重复的索引

要检查Pro或Starter云架构上是否存在重复的索引，请运行以下SQL查询。

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

查询会返回任何重复索引的列名称和名称。

专业建筑商也可以使用Percona Toolkit运行检查  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` 命令。

### 删除重复的索引

使用SQL [DROP INDEX语句](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) 删除重复的索引。

```SQL
DROP INDEX
```

## 其他信息

[云部署的数据库配置最佳实践](../planning/database-on-cloud.md)

