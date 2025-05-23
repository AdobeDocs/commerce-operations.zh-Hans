---
title: 解决数据库性能问题的最佳实践
description: 了解如何修复在云基础架构上部署的Adobe Commerce站点上导致性能下降的数据库问题。
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# 解决数据库性能问题的最佳实践

本文讨论如何修复对云基础架构站点上的Adobe Commerce上的数据库性能产生负面影响的数据库问题。

## 受影响的版本

云基础架构上的Adobe Commerce

## 识别并解决长时间运行的查询

确定是否有运行缓慢的MySQL查询。 根据您的Adobe Commerce云基础架构计划以及相应的工具可用性，您可以执行以下操作。

### 使用MySQL分析数据库查询

您可以使用MySQL识别并解决对云基础架构项目上的任何Adobe Commerce长时间运行的查询。

1. 运行[`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html)语句。
1. 如果看到长时间运行的查询，请为每个查询运行[MySQL `EXPLAIN`和`EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/)，以了解是什么导致查询长时间运行。
1. 根据发现的问题，采取措施修复查询，使其更快地运行。

### 使用Percona Toolkit分析查询（仅适用于Pro体系结构）

如果您的Adobe Commerce项目部署在Pro体系结构上，则可以使用Percona工具包来分析查询。

1. 对MySQL慢查询日志运行`pt-query-digest --type=slowlog`命令。
   * 要查找慢查询日志的位置，请参阅我们的开发人员文档中的&#x200B;**[!UICONTROL Log locations > Service Logs]**(https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/test/log-locations#service-logs)。
   * 请参阅[Percona工具包> pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest)文档。
1. 根据发现的问题，采取措施修复查询，使其更快地运行。

## 验证所有表是否都有主键

定义主键是良好的数据库和表设计的要求。 主键提供了一种方法，用于唯一标识任何表中的单行。

如果您的表没有主键，则Adobe Commerce的默认数据库引擎(InnoDB)使用第一个唯一的not null键作为主键。 如果没有唯一键可用，InnoDB将创建一个隐藏的主键（6字节）。 隐式定义的主键的问题在于您无权控制它。 此外，隐式值是为所有没有主键的表全局分配的。 如果对这些表执行同时写入，此配置可能会导致争用问题。 这可能会导致性能问题，因为表也共享全局隐藏的主键索引增量。

通过为任何没有主键的表定义主键来防止出现这些问题。

### 标识和更新没有主键的表

1. 使用以下SQL查询标识没有主键的表：

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. 对于任何缺少主键的表，请通过用类似于以下内容的节点更新`db_schema.xml`（声明性架构）来添加主键：

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   添加节点时，请将`referenceID`和`column name`变量替换为自定义自定义值。

有关详细信息，请参阅我们的开发人员文档中的[配置声明性架构](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/)。

## 识别并删除重复索引

识别数据库中的任何重复索引并将其删除。

### 检查重复的索引

要检查Pro或Starter云架构上的重复索引，请运行以下SQL查询。

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

查询返回列名和任何重复索引的名称。

专业架构商也可以使用Percona Toolkit `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)`命令运行检查。

### 删除重复的索引

使用SQL [DROP INDEX语句](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html)删除重复的索引。

```SQL
DROP INDEX
```

## 其他信息

[云部署的数据库配置最佳实践](../planning/database-on-cloud.md)
