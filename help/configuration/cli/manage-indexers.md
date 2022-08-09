---
title: 管理索引器
description: 请参阅有关如何查看和管理商务索引器的示例。
source-git-commit: dd84039be22b6bd25d57912615d64bad91970926
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# 管理索引器

{{file-system-owner}}

要查看所有索引器的列表，请执行以下操作：

```bash
bin/magento indexer:info
```

该列表如下所示：

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

## 查看索引器状态

使用此命令可查看所有索引器或特定索引器的状态。 例如，了解索引器是否需要重新编入索引。

命令选项：

```bash
bin/magento indexer:status [indexer]
```

其中 `[indexer]` 是索引器以空格分隔的列表。 省略 `[indexer]` 查看所有索引器的状态。

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

使用此命令仅一次重新索引所有或选定的索引器。

>[!INFO]
>
>此命令仅重新索引一次。 要使索引器保持为最新，您必须设置 [cron作业](../cli/configure-cron-jobs.md).

命令选项：

```bash
bin/magento indexer:reindex [indexer]
```

其中 `[indexer]` 是索引器以空格分隔的列表。 省略 `[indexer]` 重新编入所有索引器的索引。

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
>对于拥有大量产品、客户、类别和促销规则的商店，重新索引所有索引器可能需要很长时间。

### 在并行模式下重新索引

索引器的范围是多线程的，以支持在并行模式下重新索引。 它按索引器的维度并行并跨多个线程执行，从而减少处理时间。

在这方面， `dimension` 是重新索引的范围，例如 `website` 或者只是特定的 `customer_group`.

索引并行化仅影响范围内的索引器，这意味着Commerce使用索引器作为其范围将数据拆分为多个表，而不是将所有数据保留在一个表中。

您可以在并行模式下运行以下索引：

- `Catalog Search Fulltext` 可以用商店的景观来并行。
- `Category Product` 可以用商店的景观来并行。
- `Catalog Price` 网站和客户群可以并行进行。
- `Catalog Permissions` 可以由客户团队来并行处理。

要使用并行化，请为产品价格索引器设置一个可用的维度模式：

- `none` （默认）
- `website`
- `customer_group`
- `website_and_customer_group`

例如，要设置每个网站的模式：

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

要对目录权限使用并行化，请为目录权限索引器设置一个可用的维度模式：

- `none` （默认）
- `customer_group`

或者，要检查当前模式：

```bash
bin/magento indexer:show-dimensions-mode
```

要在并行模式下重新编入索引，请使用环境变量运行reindex命令 `MAGE_INDEXER_THREADS_COUNT`，或向 `env.php` 文件。 此变量设置重新索引处理的线程数。

例如，以下命令运行 `Catalog Search Fulltext` 跨三个线程的索引器：

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## 重置索引器

使用此命令可使所有索引器或特定索引器的状态失效。

命令选项：

```bash
bin/magento indexer:reset [indexer]
```

其中 ```[indexer]``` 是索引器以空格分隔的列表。 省略 `[indexer]` 使所有索引器失效。

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

使用此命令设置以下索引器选项：

- **保存时更新(`realtime`)**:当在管理员中进行更改时，将更新索引数据。 （例如，将产品添加到“管理员”中的类别后，将重新编入类别产品索引。） 这是默认设置。
- **按计划更新(`schedule`)**:数据将根据您的cron作业设置的计划进行索引。

[了解有关索引的更多信息](https://developer.adobe.com/commerce/php/development/components/indexing/).

### 显示当前配置

要查看当前索引器配置，请执行以下操作：

```bash
bin/magento indexer:show-mode [indexer]
```

其中 `[indexer]` 是索引器以空格分隔的列表。 省略 `[indexer]` 以显示所有索引器模式。 例如，要显示所有索引器的模式：

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
>在切换索引器模式之前，我们建议将您的网站置于 [维护](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html) 模式和 [禁用cron作业](https://devdocs.magento.com/cloud/configure/setup-cron-jobs.html#disable-cron-jobs). 这可确保您不会遭受数据库锁定。

要指定索引器配置，请执行以下操作：

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

其中：

- `realtime` — 设置选定的索引器以在保存时更新。
- `schedule` — 根据cron计划设置要保存的指定索引器。
- `indexer` — 索引器的列表以空格分隔。 省略 `indexer` 以相同方式配置所有索引器。

例如，要仅更改类别产品和产品类别索引器以按计划更新，请输入：

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

示例结果：

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

当索引器模式设置为 `schedule` 在索引器模式设置为 `realtime`. 如果在将索引器设置为 `schedule`，请将索引器更改为 `realtime` 然后把它们改回 `schedule`. 这会重置触发器。
