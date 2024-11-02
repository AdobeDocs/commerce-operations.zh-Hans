---
title: 云部署的数据库配置最佳实践
description: 了解如何在云基础架构上部署Adobe Commerce时配置数据库和应用程序设置以提高性能。
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# 数据库配置的最佳实践

了解在云基础架构上部署Adobe Commerce时提高数据库性能并高效使用数据库的最佳实践。

## 受影响的产品

云基础架构上的Adobe Commerce

## 将所有MyISAM表转换为InnoDB

Adobe建议使用InnoDB数据库引擎。 在默认的Adobe Commerce安装中，数据库中的所有表都使用InnoDB引擎进行存储。 但是，某些第三方模块（扩展）可能会以MyISAM格式引入表。 安装第三方模块后，请检查数据库以识别`myisam`格式的所有表并将其转换为`innodb`格式。

### 确定模块是否包含MyISAM表

您可以在安装第三方模块代码之前对其进行分析，以确定它是否使用MyISAM表。

如果已安装扩展，请运行以下查询以确定数据库是否具有任何MyISAM表：

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### 将存储引擎更改为InnoDB

在声明表的`db_schema.xml`文件中，将相应`table`节点的`engine`属性值设置为`innodb`。 有关参考，请参阅我们的开发人员文档中的[配置声明性架构>表节点](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/)。

声明性方案在Adobe Commerce中引入，用于云基础架构版本2.3。

## 为本机MySQL搜索配置推荐的搜索引擎

Adobe建议，即使您计划为Adobe Commerce应用程序配置第三方搜索工具，也始终为云基础架构项目上的Adobe Commerce设置Elasticsearch或OpenSearch。 此配置提供了第三方搜索工具发生故障时的回退选项。

您使用的搜索引擎取决于安装的云版Adobe Commerce：

- 对于Adobe Commerce 2.4.4及更高版本，请使用OpenSearch服务进行本机MySQL搜索。

- 对于较早的Adobe Commerce版本，请使用Elasticsearch。

要确定当前使用的搜索引擎，请运行以下命令：

```bash
./bin/magento config:show catalog/search/engine
```

有关配置说明，请参阅云上Adobe Commerce的《开发人员指南》 ：

- [设置OpenSearch服务](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)

- [设置Elasticsearch服务](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)

## 避免自定义触发器

如果可能，请避免使用自定义触发器。

触发器用于将更改记录到审核表中。 出于以下原因，Adobe建议将应用程序配置为直接写入审计表，而不是使用“触发”功能：

- 触发器被解释为代码，并且MySQL不预编译它们。 挂接到查询的事务空间后，它们将开销添加到解析器和解释器，以解释使用表执行的每个查询。
- 触发器与原始查询共享相同的事务空间，当这些查询争夺表上的锁时，触发器会独立地争夺另一个表上的锁。

要了解使用自定义触发器的替代方法，请参阅[MySQL触发器](mysql-configuration.md#triggers)。

## 将[!DNL ECE-Tools]升级到版本2002.0.21或更高版本 {#ece-tools-version}

要避免cron死锁的潜在问题，请将ECE-Tools升级到2002.0.21或更高版本。 有关说明，请参阅我们的开发人员文档中的[更新`ece-tools`版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package)。

## 安全切换索引器模式

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

切换索引器将生成[!DNL data definition language] (DDL)语句以创建可能导致数据库锁定的触发器。 您可以在更改配置之前，通过将网站置于维护模式并禁用cron作业来防止出现此问题。
有关说明，请参阅*Adobe Commerce配置指南*&#x200B;中的[配置索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1)。

## 不要在生产环境中运行DDL语句

避免在生产环境中运行DDL语句以防止冲突（如表修改和创建）。 `setup:upgrade`进程是一个异常。

如果需要运行DDL语句，请将网站置于维护模式并禁用cron（请参阅上一节中有关安全切换索引的说明）。

## 启用订单存档

从管理员处启用订单存档，以随着订单数据的增长而减少销售表所需的空间。 存档可节省MySQL磁盘空间并提高签出性能。

请参阅Adobe Commerce商家文档中的[启用存档](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html)。

## 其他信息

- [MySQL存储引擎](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Adobe Commerce 2.3.5升级MariaDB的先决条件](../maintenance/mariadb-upgrade.md)
- [解决数据库性能问题的最佳实践](../maintenance/resolve-database-performance-issues.md)
