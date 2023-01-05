---
title: 云部署的数据库配置最佳实践
description: 了解在云基础架构上部署Adobe Commerce时，如何配置数据库和应用程序设置以提高性能。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---

# 数据库配置的最佳实践

了解在云基础架构上部署Adobe Commerce时提高数据库性能并高效使用数据库的最佳实践。

## 受影响的产品

Adobe Commerce云基础架构

## 将所有MyISAM表转换为InnoDB

Adobe建议使用InnoDB数据库引擎。 在默认的Adobe Commerce安装中，数据库中的所有表都使用InnoDB引擎进行存储。 但是，某些第三方模块（扩展）可以引入MyISAM格式的表。 安装第三方模块后，请检查数据库以标识 `myisam` 设置格式并将其转换为 `innodb` 格式。

### 确定模块是否包含MyISAM表

您可以在安装第三方模块代码之前对其进行分析，以确定它是否使用MyISAM表。

如果已安装扩展，请运行以下查询以确定数据库是否具有任何MyISAM表：

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### 将存储引擎更改为InnoDB

在 `db_schema.xml` 文件声明表，设置 `engine` 属性值 `table` 节点到 `innodb`. 有关参考，请参阅 [配置声明性架构>表节点](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) ，请参阅我们的开发人员文档。

在云基础架构版本2.3的Adobe Commerce中引入了声明性方案。

## 为本机MySQL搜索配置推荐的搜索引擎

Adobe建议您始终在云基础架构项目上为Adobe Commerce设置Elasticsearch或OpenSearch，即使您计划为Adobe Commerce应用程序配置第三方搜索工具也是如此。 此配置提供了一个回退选项，以防第三方搜索工具失败。

您使用的搜索引擎取决于安装的云版本上的Adobe Commerce:

- 对于Adobe Commerce 2.4.4及更高版本，请使用OpenSearch服务进行本机MySQL搜索。

- 对于早期的Adobe Commerce版本，请使用Elasticsearch。

要确定当前使用的搜索引擎，请运行以下命令：

```bash
./bin/magento config:show catalog/search/engine
```

有关配置说明，请参阅云上Adobe Commerce开发人员指南：

- [设置OpenSearch服务](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [设置Elasticsearch服务](https://devdocs.magento.com/cloud/project/services-elastic.html)

## 避免自定义触发器

尽量避免使用自定义触发器。

触发器用于将更改记录到审核表中。 Adobe建议将应用程序配置为直接写入审核表，而不是使用触发器功能，原因如下：

- 触发器将解释为代码，MySQL不会预编译它们。 关联到查询的事务空间后，它们会为通过表执行的每个查询向解析器和解释器添加开销。
- 触发器与原始查询共享相同的事务空间，并且当这些查询争用表上的锁时，触发器独立地竞争另一表上的锁。

要了解使用自定义触发器的替代方法，请参阅 [有效使用MySQL触发器](mysql-triggers-usage.md) 在我们的支持知识库中。

## 升级 [!DNL ECE-Tools] 到2002.0.21或更高版本 {#ece-tools-version}

为避免CRON死锁的潜在问题，请将ECE-Tools升级到版本2002.0.21或更高版本。 有关说明，请参阅 [更新 `ece-tools` 版本](https://devdocs.magento.com/cloud/project/ece-tools-update.html) ，请参阅我们的开发人员文档。

## 安全切换索引器模式

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

切换索引器生成 [!DNL data definition language] (DDL)语句，以创建可导致数据库锁定的触发器。 您可以通过将网站置于维护模式并在更改配置之前禁用cron作业来防止此问题。
有关说明，请参阅 [配置索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) 在 *Adobe Commerce配置指南*.

## 不在生产中运行DDL语句

避免在生产环境中运行DDL语句以防止冲突（如表的修改和创建）。 的 `setup:upgrade` 进程是例外。

如果需要运行DDL语句，请将网站置于维护模式并禁用cron（请参阅上一节中有关安全切换索引的说明）。

## 启用订单存档

允许管理员对订单进行归档，以在订单数据增长时减少销售表所需的空间。 存档可节省MySQL磁盘空间并提高签出性能。

请参阅 [启用存档](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) ，位于Adobe Commerce Merchant文档中。

## 其他信息

- [MySQL存储引擎](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Adobe Commerce 2.3.5升级MariaDB先决条件](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [解决数据库性能问题的最佳实践](../maintenance/resolve-database-performance-issues.md)
