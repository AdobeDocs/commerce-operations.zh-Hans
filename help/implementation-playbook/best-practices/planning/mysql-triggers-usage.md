---
title: MySQL触发器用法
description: 了解如何将MySQL触发器与Adobe Commerce有效结合使用。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 79a825a094a80892cf1a30aa7f5c61bd351c69f5
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# 使用MySQL触发器的最佳实践

本文介绍了在使用MySQL触发器时如何避免性能问题。 触发器用于将更改记录到审核表中。

## 受影响的产品和版本

- Adobe Commerce内部
- Adobe Commerce云基础架构

>[!WARNING]
>
>对于云项目上的Adobe Commerce，在更改生产环境的配置之前，应始终在暂存环境中测试配置更改。

## 了解性能影响

触发器被解释为代码，这意味着MySQL不会预编译它们。

挂钩到查询的事务空间中，触发器会为使用表执行的每个查询向解析器和解释器添加开销。 触发器与原始查询共享相同的事务空间，并且当这些查询争用表上的锁时，触发器独立地争用另一个表上的锁。

如果使用了许多触发器，则此额外开销可能会对网站的性能造成负面影响。

>[!WARNING]
>
>Adobe Commerce不支持Adobe Commerce数据库中的任何自定义触发器，因为自定义触发器可能会引入与未来Adobe Commerce版本的不兼容性。 有关最佳实践，请参阅 [MySQL一般准则](../../../installation/prerequisites/database/mysql.md) (在Adobe Commerce文档中)。

## 有效使用触发器

要防止在使用触发器时出现性能问题，请遵循以下准则：

- 如果您有自定义触发器，在执行触发器时会写入一些数据，请移动此逻辑以直接写入审核表。 例如，通过在应用程序代码中添加附加查询，在查询之后您打算为其创建触发器。
- 查看现有的自定义触发器，并考虑删除它们并直接从应用程序端写入表。 使用 [`SHOW TRIGGERS` SQL语句](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- 如需其他帮助、问题或关切， [提交Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## 其他信息

- [MySQL先决条件](../../../installation/prerequisites/database/mysql.md)
- [云基础架构上的Adobe Commerce数据库最佳实践](database-on-cloud.md)
