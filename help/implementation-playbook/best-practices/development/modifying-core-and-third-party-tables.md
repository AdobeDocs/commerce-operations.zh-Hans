---
title: 修改数据库表的最佳实践
description: 了解如何以及何时修改Adobe Commerce和第三方数据库表。
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: d40de2f05147e6c58c15cd3cd59275cc91283162
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---

# 修改数据库表的最佳实践

本文提供了修改[!DNL Adobe Commerce]或第三方模块创建的数据库表的最佳实践。 了解何时以及如何有效修改表有助于确保商务平台的长期可行性和稳定性。

从[!DNL Magento 1]和其他电子商务平台迁移，或使用来自[!DNL Adobe Commerce] Marketplace的模块，可能需要添加和保存额外数据。 您的第一反应可能是向数据库表中添加一列，或者调整现有列。 但是，您只能在有限的情况下修改核心[!DNL Adobe Commerce]表（或第三方供应商表）。

## 为什么Adobe建议避免修改

避免修改核心表的主要原因是Adobe Commerce包含包含原始SQL查询的基础逻辑。 更改表结构可能会产生难以消除的意外副作用。 此更改还会影响DDL（数据定义语言）操作，从而导致对性能产生意外和不可预测的影响。

避免更改数据库表结构的另一个原因是，如果核心开发团队或第三方开发人员更改其数据库表的结构，则所做的更改可能会导致问题。 例如，有一些核心数据库表具有名为`additional_data`的列。 这始终是`text`列类型。 但是，出于性能原因，核心团队可能会将列更改为`longtext`。 此类型的列是JSON的别名。 通过转换为此列类型，该列中添加了性能提高和可搜索性，但该列并不作为`text`类型存在。 有关此主题的更多信息，请参阅[JSON数据类型](https://mariadb.com/kb/en/json-data-type/){target="_blank"}。

## 知道何时保存或删除数据

Adobe建议您首先确定是否需要保存此数据。 如果您从旧系统中移动数据，则可以删除的任何数据都会在迁移期间为您节省时间和精力。 （如果需要稍后访问数据，可以使用一些方法将其存档。） 要很好地管理应用程序和性能，可以质疑保存额外数据的请求。 您的目标是确保保存数据是满足以其他方式无法满足的业务需求的要求。

### 旧数据

如果您的项目包含旧数据（如旧订单或客户记录），请考虑使用替代查找方法。 例如，如果业务仅需要访问数据以供临时参考，请考虑对托管在商务平台之外的旧数据库实施外部搜索，而不是将旧数据迁移到[!DNL Adobe Commerce]。

这种情况要求将数据库迁移到服务器，提供Web界面来读取数据，或者培训使用MySQL Workbench或类似工具。 从新数据库中排除此数据可让开发团队专注于新站点，而不是排查数据迁移问题，从而加快迁移速度。

另一个让数据保留在商业外部但允许您实时使用的相关选项是利用其他工具，例如GraphQL mesh。 此选项将不同的数据源组合在一起，并将它们作为单个响应返回。

例如，您可以`stitch`将外部数据库(可能已停用的旧Magento 1站点)中的旧订单合并起来。 然后使用GraphQL网格，将它们显示为客户订单历史记录的一部分。 这些旧订单可以与当前[!DNL Adobe Commerce]环境中的订单合并。

有关将API网格用于GraphQL的更多信息，请参阅[什么是API网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"})和[GraphQL网格网关](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}。

## 使用扩展属性迁移旧数据

如果您确定旧数据需要迁移，或者新数据需要保存在[!DNL Adobe Commerce]中，Adobe建议使用[扩展属性](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}。 使用扩展属性保存其他数据具有以下优势：

- 您可以控制保留的数据和数据库结构，从而确保以正确的列类型和正确的索引保存数据。
- [!DNL Adobe Commerce]中的大多数实体都支持使用扩展属性。
- 扩展属性是一种与存储无关的机制，该机制提供了灵活性，让您可以将数据保存在项目的最佳位置。

存储位置的两个示例是数据库表和[!DNL Redis]。 在选择位置时需要考虑的关键事项是：位置会引入额外的复杂性还是影响性能。

### 考虑其他替代方案

作为开发人员，务必考虑使用[!DNL Adobe Commerce]环境之外的工具，例如GraphQL mesh和Adobe App Builder。 这些工具可以帮助您保留对数据的访问权限，但对核心商务应用程序或其底层数据库表没有影响。 通过这种方法，您可以通过API公开数据。 然后，向App Builder配置添加数据源。 使用GraphQL Mesh，您可以合并这些数据源并生成单个响应，如[旧数据](#legacy-data)中所述。

有关GraphQL Mesh的其他详细信息，请参阅[GraphQL Mesh网关](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}。 有关Adobe App Builder的信息，请参阅[App Builder简介](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=zh-Hans){target="_blank"}。

## 修改核心表或第三方表

如果决定通过修改核心[!DNL Adobe Commerce]或第三方模块数据库表来存储数据，请使用以下准则以将对稳定性和性能的影响降至最低。

- 仅添加新列。
- 永远不要修改现有列的&#x200B;_type_&#x200B;值。 例如，为满足您独特的使用案例，请勿将`integer`更改为`varchar`。
- 避免向EAV属性表添加列。 这些表已因逻辑和责任而过载。
- 在调整表之前，请确定其大小。 更改大型表会影响部署，这可能导致在应用更改时出现几分钟或几小时的延迟。

## 修改外部数据库表的最佳实践

当您将列添加到核心数据库表或第三方表时，Adobe建议执行以下步骤：

1. 在命名空间中创建具有名称的模块，该名称表示要更新的内容。

   例如： `app/code/YourCompany/Customer`

1. 创建相应的文件以启用模块（请参阅[创建模块](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html?lang=zh-Hans){target="_blank"}）。

1. 在`db_schema.xml`文件夹中创建名为`etc`的文件，并进行适当的更改。

   如果适用，请生成`db_schema_whitelist.json`文件。 有关详细信息，请参阅[声明性架构](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"}。

### 潜在影响

向外部数据库添加列可能会通过以下方式影响您的Adobe Commerce项目：

- 升级可能会更复杂。
- 如果正在修改的表很大，则部署会受到影响。
- 向新平台的迁移可能会更复杂。

## 避免修改核心表的方法

您可以避免使用[扩展属性](#migrate-legacy-data-with-extension-attributes)来修改Adobe Commerce数据库表。 另一种方法是使用在几个核心表上发现的特殊列(`additional_data`)来存储数据并将其保存为JSON编码格式。

### 将数据保存在JSON编码的数据列中

某些核心表具有包含JSON编码数据的`additional_data`列。 此列提供了一种将其他数据映射到一个字段中的本机方式。 使用该方法可避免添加用于小的、简单的数据元素的表，所述表存储用于数据检索的信息而无需搜索要求。 `additional_data`列通常仅在项目级别可用，不适用于整个报价或订单。

- 使用`additional_data`字段的优势

   - 无需其他字段，这样可保持列数最小。 这在销售流程中很有用，因为销售流程中已涉及许多表。 最好不要给这个本已复杂的过程增加更多的复杂性。 该方法能满足多种使用场合，但不是全部。

- 缺点

   - 此方法仅适用于存储只读数据。 出现此问题是因为需要取消序列化我们的代码才能修改和构建对象以添加依赖项或数据库关系。

   - 使用数据库操作查找这些字段很困难。 使用此方法搜索时速度较慢。

   - 在`additional_data`列中存储数据时必须格外小心，以免触发序列化或取消序列化操作，这些操作可能会通过创建无效的JSON来中断代码，或在运行时导致读取错误。

   - 这些字段必须在代码中明确声明，以便开发人员可以轻松找到它们。

   - 其他可能发生且很难诊断的问题。 例如，对于某些本机PHP函数，如果您不使用核心应用程序提供的[!DNL Adobe Commerce]包装器方法，则转换数据的结束结果可能与预期格式不同。 应始终使用包装器函数以确保保存或检索的数据的一致性和可预测性。

以下是具有`additional_data`列的列和结构的表的示例。

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

在版本2.4.3、2.4.4和2.4.5中，有十个表具有列`additional_data`。

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```
