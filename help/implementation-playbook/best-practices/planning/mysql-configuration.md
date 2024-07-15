---
title: MySQL配置最佳实践
description: 了解MySQL触发器和从属连接如何影响Commerce站点性能以及如何有效使用它们。
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# MySQL配置最佳实践

>[!NOTE]
>
>此主题包含行业标准软件术语，有些人可能会认为这些术语具有种族主义、性别歧视或压迫性，并且可能会使读者感到伤害、创伤或不受欢迎。 Adobe正在努力从代码、文档和用户体验中删除这些术语。

## 触发器

本文介绍了在使用MySQL触发器时如何避免出现性能问题。 触发器用于将更改记录到审核表中。

### 受影响的产品和版本

- Adobe Commerce内部部署
- 云基础架构上的Adobe Commerce

>[!WARNING]
>
>对于云项目上的Adobe Commerce，在更改生产环境的配置之前，请始终在暂存环境中测试配置更改。

### 性能影响

触发器被解释为代码，这意味着MySQL不会预编译它们。

挂接到查询的事务空间时，会触发向解析器和解释器添加开销，以解释使用表执行的每个查询。 触发器与原始查询共享相同的事务空间，当这些查询争夺表上的锁时，触发器会独立争夺另一个表上的锁。

如果使用许多触发器，这些额外的开销可能会对站点的站点性能产生负面影响。

>[!WARNING]
>
>Adobe Commerce不支持Adobe Commerce数据库中的任何自定义触发器，因为自定义触发器可能会与将来的Adobe Commerce版本不兼容。 有关最佳实践，请参阅Adobe Commerce文档中的[一般MySQL准则](../../../installation/prerequisites/database/mysql.md)。

### 有效使用

要防止在使用触发器时出现性能问题，请遵循以下准则：

- 如果您有在执行触发器时写入某些数据的自定义触发器，请将此逻辑移动到直接写入审计表。 例如，通过在应用程序代码中添加其他查询，在要为其创建触发器的查询之后。
- 查看现有的自定义触发器，并考虑删除它们并直接从应用程序端写入表。 使用[`SHOW TRIGGERS` SQL语句](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html)检查数据库中的现有触发器。
- 如需其他帮助、问题或顾虑，请[提交Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket)。

## 从属连接

Adobe Commerce可以异步读取多个数据库。 如果您预计部署在云基础架构Pro体系结构上的Commerce站点的MySQL数据库负载会很高，则Adobe建议启用MYSQL从属连接。

启用MYSQL从属连接时，Adobe Commerce使用到数据库的只读连接来接收非主节点上的只读通信。 当只有一个节点处理读写通信时，通过负载平衡提高了性能。

### 受影响的版本

云基础架构上的Adobe Commerce，仅限Pro架构

### 配置

在云基础架构上的Adobe Commerce中，您可以通过设置[MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection)变量来覆盖MYSQL从属连接的默认配置。 将此变量设置为`true`可自动使用到数据库的只读连接。

**启用MySQL从属连接**：

1. 在本地工作站上，转到您的项目目录。

1. 在`.magento.env.yaml`文件中，将`MYSQL_USE_SLAVE_CONNECTION`设置为true。

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 提交`.magento.env.yaml`文件更改并推送到远程环境。

   成功完成部署后，将为云环境启用MySQL从属连接。
