---
title: 管理索引器
description: 请参阅有关如何查看和管理Commerce索引器的示例。
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 8b9e4de2799532e4654fce63d856c2d301025f09
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 管理索引器

{{file-system-owner}}

要查看所有索引器的列表，请执行以下操作：

```bash
bin/magento indexer:info
```

该列表显示如下：

```terminal
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

>[!NOTE]
> 使用Live Search、Catalog Service或Product Recommendations的Adobe Commerce商家可以选择使用 [基于SaaS的价格索引](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## 查看索引器状态

使用此命令可以查看所有索引器或特定索引器的状态。 例如，了解索引器是否需要重新索引。

命令选项：

```bash
bin/magento indexer:status [indexer]
```

位置 `[indexer]` 是以空格分隔的索引器列表。 省略 `[indexer]` 以查看所有索引器的状态。

示例结果：

```terminal
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## 重新索引

使用此命令可只重新索引一次所有或选定的索引器。

>[!INFO]
>
>此命令只重新索引一次。 要使索引器保持最新，您必须设置 [cron作业](../cli/configure-cron-jobs.md).

命令选项：

```bash
bin/magento indexer:reindex [indexer]
```

位置 `[indexer]` 是以空格分隔的索引器列表。 省略 `[indexer]` 重新索引所有索引器。

示例结果：

```terminal
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>对于具有大量产品、客户、类别和促销规则的商店，重新索引所有索引器可能需要很长时间。

### 以并行模式重新索引

{{php-process-control}}

索引器具有作用域和多线程，以支持在并行模式下重新索引。 它通过索引器的维度进行并行，并在多个线程中执行，从而缩短处理时间。

在这种情况下， `dimension` 是重新索引的范围，例如 `website` 或只是特定的 `customer_group`.

索引并行化仅影响作用域的索引器，这意味着Commerce使用索引器作为其作用域将数据拆分为多个表，而不是将所有数据保留在一个表中。

您可以在并行模式下运行以下索引：

- `Catalog Search Fulltext` 可按商店查看次数并行。
- `Category Product` 可按商店查看次数并行。
- `Catalog Price` 可由网站和客户组并行。
- `Catalog Permissions` 可以由客户组并行。

>[!INFO]
>
>默认情况下，目录搜索全文和类别产品的并行处于启用状态。

要使用并行化，请为产品价格索引器设置一种可用的维度模式：

- `none` （默认）
- `website`
- `customer_group`
- `website_and_customer_group`

例如，为每个网站设置模式：

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

要对目录权限使用并行化，请为目录权限索引器设置一种可用的维度模式：

- `none` （默认）
- `customer_group`

或者检查当前模式：

```bash
bin/magento indexer:show-dimensions-mode
```

要在并行模式下重新索引，请使用环境变量运行reindex命令 `MAGE_INDEXER_THREADS_COUNT`，或将环境变量添加到 `env.php` 文件。 此变量设置用于重新索引处理的线程数。

例如，以下命令运行 `Catalog Search Fulltext` 索引器跨三个线程：

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## 重置索引器

使用此命令可使所有索引器或特定索引器的状态失效。

命令选项：

```bash
bin/magento indexer:reset [indexer]
```

位置 ```[indexer]``` 是以空格分隔的索引器列表。 省略 `[indexer]` 使所有索引器失效。

示例结果：

```terminal
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## 配置索引器

使用此命令可设置以下索引器选项：

- **保存时更新(`realtime`)**：在管理员中进行更改后，索引数据会更新。 （例如，将产品添加到管理员中的类别后，会重新索引类别产品索引。） 这是默认设置。
- **按计划更新(`schedule`)**：根据cron作业设置的时间表为数据编制索引。

[了解有关索引的更多信息](https://developer.adobe.com/commerce/php/development/components/indexing/).

### 显示当前配置

要查看当前索引器配置，请执行以下操作：

```bash
bin/magento indexer:show-mode [indexer]
```

位置 `[indexer]` 是以空格分隔的索引器列表。 省略 `[indexer]` 以显示所有索引器的模式。 例如，要显示所有索引器的模式，请执行以下操作：

示例结果：

```terminal
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### 配置索引器

>[!INFO]
>
>在切换索引器模式之前，我们建议将您的网站放在 [维护](../../installation/tutorials/maintenance-mode.md) 模式和 [禁用cron作业](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). 这可以确保您不会遇到数据库锁定的问题。

要指定索引器配置，请执行以下操作：

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

其中：

- `realtime` — 设置所选索引器在保存时更新。
- `schedule` — 根据cron计划设置要保存的指定索引器。
- `indexer` — 以空格分隔的索引器列表。 省略 `indexer` 以相同方式配置所有索引器。

例如，要仅更改按计划更新的类别产品和产品类别索引器，请输入：

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

示例结果：

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

当索引器模式设置为时，将添加与索引器相关的数据库触发器 `schedule` 并将索引器模式设置为时删除 `realtime`. 当索引器设置为时，如果数据库中缺少触发器 `schedule`，将索引器更改为 `realtime` 然后改回 `schedule`. 这将重置触发器。
