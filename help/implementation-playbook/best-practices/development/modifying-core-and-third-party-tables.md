---
title: 修改数据库表的最佳实践
description: 了解如何以及何时修改Adobe Commerce和第三方数据库表。
role: Developer, Architect
feature: Best Practices
feature-set: Commerce
last-substantial-update: 2022-11-15T00:00:00Z
source-git-commit: 570fa4877f578f636736f0404169ed215fd06b24
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 0%

---

# 修改数据库表的最佳实践

本文提供了修改由创建的数据库表的最佳实践 [!DNL Adobe Commerce] 或第三方模块。 了解何时以及如何有效地修改表有助于确保商务平台的长期可行性和稳定性。

从迁移 [!DNL Magento 1] 和其他电子商务平台，或使用 [!DNL Adobe Commerce] Marketplace可能需要添加和保存额外数据。 您的第一反应可能是向数据库表中添加列，或调整现有列。 但是，您只应修改核心 [!DNL Adobe Commerce] 表（或第三方供应商表）。

## 为何Adobe建议避免修改

避免修改核心表的主要原因是，Adobe Commerce包含包含原始SQL查询的基础逻辑。 更改表的结构可能会导致意外的副作用，这些副作用很难进行故障诊断。 此更改还会影响DDL（数据定义语言）操作，从而对性能造成意外和不可预知的影响。

避免更改数据库表结构的另一个原因是，如果核心开发团队或第三方开发人员更改其数据库表结构，则所做的更改可能会导致问题。 例如，有一些核心数据库表具有一个名为 `additional_data`. 这一直是 `text` 列类型。 但是，出于性能原因，核心团队可能会将列更改为 `longtext`. 此类列是JSON的别名。 通过转换为此列类型，向该列添加了性能提升和可搜索性，但该列不存在 `text` 类型。 您可以在 [JSON数据类型](https://mariadb.com/kb/en/json-data-type/){target=&quot;_blank&quot;}。

## 了解何时保存或删除数据

Adobe建议您首先确定是否需要保存此数据。 如果您从旧版系统移动数据，则可以删除的任何数据都会在迁移过程中节省您的时间和精力。 （如果以后需要访问数据，可以使用多种方法对其进行存档。） 为了更好地管理应用程序和性能，可以质疑保存额外数据的请求。 您的目标是确保保存数据是满足无法以其他方式填写的业务需求的一项要求。

### 旧版数据

如果您的项目包含旧数据（如旧订单或客户记录），请考虑使用替代查找方法。 例如，如果业务需要访问数据仅供偶尔参考，请考虑对商务平台外托管的旧数据库实施外部搜索，而不是将旧数据迁移到 [!DNL Adobe Commerce].

这种情况需要将数据库迁移到服务器，提供用于读取数据的Web界面，或者培训MySQL Workbench或类似工具的使用。 将此数据从新数据库中排除会加快迁移速度，因为开发团队可以专注于新站点，而不是对数据迁移问题进行故障排除。

另一个用于将数据保留在商务外部但允许您实时使用的相关选项是利用其他工具，如GraphQL网格。 此选项将不同的数据源组合在一起，并作为单个响应返回它们。

例如，您可以 `stitch` 将外部数据库的旧订单(可能是已停用的旧Magento1站点)合起来。 然后，使用GraphQL网格，将它们显示为客户订单历史记录的一部分。 这些旧订单可以与您当前的订单组合 [!DNL Adobe Commerce] 环境。

有关将API网格与GraphQL结合使用的更多信息，请参阅 [什么是API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target=&quot;_blank&quot;})和 [GraphQL Mesh网关](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}。

## 使用扩展属性迁移旧版数据

如果您确定旧数据需要迁移，或新数据需要保存在 [!DNL Adobe Commerce],Adobe建议使用 [扩展属性](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target=&quot;_blank&quot;}。 使用扩展属性保存其他数据具有以下优势：

- 您可以控制要保留的数据和数据库结构，这可确保使用正确的列类型和适当的索引来保存数据。
- 中的大多数实体 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 支持使用扩展属性。
- 扩展属性是一种与存储无关的机制，它允许灵活地将数据保存在项目的最佳位置。

存储位置的两个示例是数据库表和 [!DNL Redis]. 选择位置时需要考虑的关键因素是位置是否会带来额外的复杂性或影响性能。

### 考虑其他替代方案

作为开发人员，务必始终考虑在 [!DNL Adobe Commerce] 环境，如GraphQL网格和Adobe应用程序生成器。 这些工具可帮助您保留对数据的访问权，但对核心商务应用程序或其基础数据库表没有影响。 使用此方法，您可以通过API公开数据。 然后，向应用程序生成器配置中添加数据源。 使用GraphQL网格，您可以合并这些数据源并生成单个响应，如 [旧数据](#legacy-data).

有关GraphQL网格的其他详细信息，请参阅 [GraphQL Mesh网关](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}。 有关Adobe应用程序生成器的信息，请参阅 [应用程序生成器简介](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target=&quot;_blank&quot;}。

## 修改核心表或第三方表

如果您决定通过修改核心来存储数据 [!DNL Adobe Commerce] 或第三方模块数据库表，请使用以下指南来最大限度地减少对稳定性和性能的影响。

- 仅添加新列。
- 切勿修改 _type_ 现有列的值。 例如，请勿更改 `integer` 至 `varchar` 以满足您的独特用例。
- 避免向EAV属性表添加列。 这些表已经过载了逻辑和责任。
- 在调整表之前，请确定其大小。 更改大表会影响部署，在应用更改时，这可能会导致数分钟或数小时的延迟。

## 修改外部数据库表的最佳实践

Adobe建议在向核心数据库表或第三方表添加列时执行以下步骤：

1. 在命名空间中创建一个名称代表要更新内容的模块。

   例如： `app/code/YourCompany/Customer`

1. 创建相应的文件以启用模块(请参阅 [创建模块](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target=&quot;_blank&quot;}。

1. 创建一个名为 `db_schema.xml` 在 `etc` ，并进行相应的更改。

   如果适用，请生成 `db_schema_whitelist.json` 文件。 请参阅 [声明性架构](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target=&quot;_blank&quot;}以了解详细信息。

### 潜在影响

向外部数据库添加列可能会通过以下方式影响Adobe Commerce项目：

- 升级可能会更加复杂。
- 如果修改的表较大，则部署会受到影响。
- 迁移到新平台可能会更加复杂。

## 避免修改核心表的方法

您可以避免使用 [扩展属性](#migrate-legacy-data-with-extension-attributes). 另一种方法是使用特殊列(`additional_data`)以存储数据并以JSON编码格式进行保存。

### 将数据保存在JSON编码的数据列中

某些核心表具有 `additional_data` 包含JSON编码数据的列。 此列提供了在一个字段中映射附加数据的本机方式。 使用此方法可避免为存储用于数据检索的信息的简单、小的数据元素添加表，而无需搜索。 的 `additional_data` 列通常仅在项目级别可用，而不适用于整个报价或订单。

- 使用的优势 `additional_data` 字段

   - 无需其他字段，这样可保持最少列数。 在销售流程中，这非常有用，因为在销售流程中已涉及许多表。 最好不要给这个本已复杂的过程增加更多的复杂性。 此方法满足许多用例，但并非全部。

- 缺点

   - 此方法仅适用于存储只读数据。 出现此问题的原因是需要取消序列化我们的代码以修改和构建对象以添加依赖关系或数据库关系。

   - 很难使用数据库操作来搜索这些字段。 使用此方法搜索速度较慢。

   - 在 `additional_data` 列，以避免触发序列化或取消序列化操作，这些操作可能会通过创建无效JSON或在运行时导致读取错误来破坏代码。

   - 必须在代码中明确声明这些字段，以便开发人员可以轻松找到它们。

   - 可能出现的其他可能很难诊断的问题。 例如，如果不使用 [!DNL Adobe Commerce] 由核心应用提供的包装方法，转换数据的最终结果可以不同于预期的格式。 请始终使用包装函数来确保保存或检索的数据的一致性和可预测性。

以下是具有 `additional_data` 列。

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

在版本2.4.3、2.4.4和2.4.5中，有十个表具有列 `additional_data`.

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
