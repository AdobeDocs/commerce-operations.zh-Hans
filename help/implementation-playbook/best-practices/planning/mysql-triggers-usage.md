---
title: MySQL触发器使用情况
description: 了解如何通过Adobe Commerce有效使用MySQL触发器。
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: acac3e47-67c8-4eea-80e3-e26f2854391a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# MySQL触发器使用的最佳实践

本文介绍了在使用MySQL触发器时如何避免出现性能问题。 触发器用于将更改记录到审核表中。

## 受影响的产品和版本

- Adobe Commerce内部部署
- 云基础架构上的Adobe Commerce

>[!WARNING]
>
>对于云项目上的Adobe Commerce，在更改生产环境的配置之前，请始终在暂存环境中测试配置更改。

## 了解性能影响

触发器被解释为代码，这意味着MySQL不会预编译它们。

挂接到查询的事务空间时，触发器会为使用表执行的每个查询向解析器和解释器添加开销。 触发器与原始查询共享相同的事务空间，当这些查询争夺表上的锁时，触发器会独立地争夺另一个表上的锁。

如果使用许多触发器，这种额外的开销可能会对站点性能产生负面影响。

>[!WARNING]
>
>Adobe Commerce不支持Adobe Commerce数据库中的任何自定义触发器，因为自定义触发器可能会与将来的Adobe Commerce版本不兼容。 有关最佳实践，请参阅 [常规MySQL准则](../../../installation/prerequisites/database/mysql.md) 在Adobe Commerce文档中。

## 有效地使用触发器

要防止在使用触发器时出现性能问题，请遵循以下准则：

- 如果您有在执行触发器时写入某些数据的自定义触发器，请将此逻辑移动到直接写入审计表。 例如，通过在应用程序代码中添加其他查询，在要为其创建触发器的查询之后。
- 查看现有自定义触发器，并考虑删除它们并直接从应用程序端写入表。 通过使用，检查数据库中的现有触发器 [`SHOW TRIGGERS` SQL语句](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- 如需要更多帮助、疑问或顾虑， [提交Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## 其他信息

- [MySQL先决条件](../../../installation/prerequisites/database/mysql.md)
- [云基础架构上Adobe Commerce的数据库最佳实践](database-on-cloud.md)
