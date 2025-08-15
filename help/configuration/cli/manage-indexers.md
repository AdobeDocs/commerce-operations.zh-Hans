---
title: 管理索引器
description: 请参阅有关如何查看和管理Commerce索引器的示例。
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: ceefb9371dd0a85046cc5bfc0ddc72144d649608
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# 管理索引器

{{file-system-owner}}

要查看所有索引器的列表，请执行以下操作：

```bash
bin/magento indexer:info
```

该列表显示如下：

```text
cataloginventory_stock                   Stock
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalog_product_price                    Product Price
catalogrule_product                      Catalog Product Rule
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
sales_order_data_exporter                Sales Order Feed
sales_order_status_data_exporter         Sales Order Statuses Feed
store_data_exporter                      Stores Feed
```

>[!NOTE]
>
> 使用实时搜索、目录服务或产品推荐的Adobe Commerce商家可以选择使用基于[SaaS的价格索引](https://experienceleague.adobe.com/en/docs/commerce/price-indexer/price-indexing)。

## 查看索引器状态

使用此命令可以查看所有索引器或特定索引器的状态。 例如，了解索引器是否需要重新索引。

命令选项：

```bash
bin/magento indexer:status [indexer]
```

其中`[indexer]`是以空格分隔的索引器列表。 省略`[indexer]`以查看所有索引器的状态。

示例结果：

```text
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| ID                               | Title                     | Status | Update On | Schedule Status     | Schedule Updated    |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| catalogrule_product              | Catalog Product Rule      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogrule_rule                 | Catalog Rule Product      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogsearch_fulltext           | Catalog Search            | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:01:02 |
| catalog_category_product         | Category Products         | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| customer_grid                    | Customer Grid             | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| design_config_grid               | Design Config Grid        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| inventory                        | Inventory                 | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_category         | Product Categories        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| catalog_product_attribute        | Product EAV               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_price            | Product Price             | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:54 |
| targetrule_product_rule          | Product/Target Rule       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
| sales_order_data_exporter        | Sales Order Feed          | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| sales_order_status_data_exporter | Sales Order Statuses Feed | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| salesrule_rule                   | Sales Rule                | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| cataloginventory_stock           | Stock                     | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| store_data_exporter              | Stores Feed               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:11 |
| targetrule_rule_product          | Target Rule/Product       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
```

## 重新索引

使用此命令可只重新索引一次所有或选定的索引器。

>[!INFO]
>
>此命令只重新索引一次。 要使索引器保持最新，您必须设置[cron作业](../cli/configure-cron-jobs.md)。

命令选项：

```bash
bin/magento indexer:reindex [indexer]
```

其中`[indexer]`是以空格分隔的索引器列表。 省略`[indexer]`以重新索引所有索引器。

示例结果：

```text
Stock index has been rebuilt successfully in <time>
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Product/Target Rule index has been rebuilt successfully in <time>
Target Rule/Product index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
Sales Rule index has been rebuilt successfully in <time>
Sales Order Feed index has been rebuilt successfully in <time>
Sales Order Statuses Feed index has been rebuilt successfully in <time>
Stores Feed index has been rebuilt successfully in <time>
```

>[!INFO]
>
>对于具有大量产品、客户、类别和促销规则的商店，重新索引所有索引器可能需要很长时间。

### 以并行模式重新索引

{{php-process-control}}

索引器具有作用域和多线程，以支持在并行模式下重新索引。 它通过索引器的维度进行并行，并在多个线程中执行，从而缩短处理时间。

在此上下文中，`dimension`是重新索引的范围，例如为`website`或只是特定的`customer_group`。

索引并行化仅影响作用域的索引器，这意味着Commerce使用索引器作为其作用域将数据拆分为多个表，而不是将所有数据保留在一个表中。

您可以在并行模式下运行以下索引：

- `Catalog Search Fulltext`可以由存储视图并行。
- `Category Product`可以由存储视图并行。
- `Catalog Price`可由网站和客户组并行。
- `Catalog Permissions`可由客户组并行。

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

要在并行模式下重新索引，请使用环境变量`MAGE_INDEXER_THREADS_COUNT`运行reindex命令，或向`env.php`文件添加一个环境变量。 此变量设置用于重新索引处理的线程数。

例如，以下命令跨三个线程运行`Catalog Search Fulltext`索引器：

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## 重置索引器

使用此命令可使所有索引器或特定索引器的状态失效。

命令选项：

```bash
bin/magento indexer:reset [indexer]
```

其中```[indexer]```是以空格分隔的索引器列表。 省略`[indexer]`以使所有索引器失效。

示例结果：

```text
Stock indexer has been invalidated.
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Product/Target Rule indexer has been invalidated.
Target Rule/Product indexer has been invalidated.
Catalog Search indexer has been invalidated.
Sales Rule indexer has been invalidated.
Sales Order Feed indexer has been invalidated.
Sales Order Statuses Feed indexer has been invalidated.
Stores Feed indexer has been invalidated.
```

## 配置索引器

使用此命令可设置以下索引器选项：

- **保存时更新(`realtime`)**：在管理员中进行更改后，索引数据将更新。 （例如，将产品添加到管理员中的类别后，会重新索引类别产品索引。）
- **按计划(`schedule`)更新**：数据已根据cron作业设置的计划编制索引。

[了解有关索引的更多信息](https://developer.adobe.com/commerce/php/development/components/indexing/)。

### 显示当前配置

要查看当前索引器配置，请执行以下操作：

```bash
bin/magento indexer:show-mode [indexer]
```

其中`[indexer]`是以空格分隔的索引器列表。 省略`[indexer]`以显示所有索引器的模式。 例如，要显示所有索引器的模式，请执行以下操作：

示例结果：

```text
Stock:                                             Update by Schedule
Design Config Grid:                                Update by Schedule
Customer Grid:                                     Update by Schedule
Category Products:                                 Update by Schedule
Product Categories:                                Update by Schedule
Catalog Rule Product:                              Update by Schedule
Product EAV:                                       Update by Schedule
Inventory:                                         Update by Schedule
Product Price:                                     Update by Schedule
Catalog Product Rule:                              Update by Schedule
Product/Target Rule:                               Update by Schedule
Target Rule/Product:                               Update by Schedule
Catalog Search:                                    Update by Schedule
Sales Rule:                                        Update by Schedule
Sales Order Feed:                                  Update by Schedule
Sales Order Statuses Feed:                         Update by Schedule
Stores Feed:                                       Update by Schedule
```

### 设置索引器模式

>[!IMPORTANT]
>
>[!DNL Customer Grid]索引器行为在2.4.8中发生了更改：
>
>- **低于2.4.8**： [!DNL Customer Grid]索引器只能使用[!UICONTROL Update on Save]选项重新编制索引，不支持[!UICONTROL Update by Schedule]选项。
>
>   使用以下命令将此索引器设置为保存时更新：
>
>   ```bash
>   bin/magento indexer:set-mode realtime customer_grid
>   ```
>
>- **2.4.8及更高版本**： [!DNL Customer Grid]索引器同时支持[!UICONTROL Update on Save]和[!UICONTROL Update by Schedule]模式，并且默认为[!UICONTROL Update by Schedule]。
>
>请参阅[实施行动手册](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration)中的&#x200B;_索引器配置的最佳实践_。

>[!INFO]
>
>在切换索引器模式之前，请将您的网站设置为[维护](../../installation/tutorials/maintenance-mode.md)模式并[禁用cron作业](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property)。 这样可确保不会出现数据库锁定的情况。

要指定索引器配置，请执行以下操作：

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

其中：

- `realtime` — 将选定的索引器设置为在保存时更新。
- `schedule` — 根据cron计划设置要保存的指定索引器。
- `indexer` — 是索引器的空格分隔列表。 省略`indexer`以按相同方式配置所有索引器。

例如，要仅更改按计划更新的类别产品和产品类别索引器，请输入：

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

示例结果：

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

当索引器模式设置为`schedule`时，添加与索引器相关的数据库触发器；当索引器模式设置为`realtime`时，删除与索引器相关的数据库触发器。 如果索引器设置为`schedule`时数据库中缺少触发器，请将索引器更改为`realtime`，然后将它们改回`schedule`。 这将重置触发器。

### 设置索引器状态

`bin/magento indexer:set-status`命令是在Adobe Commerce 2.4.7中引入的。它允许管理员修改一个或多个索引器的运行状态，在大量操作（如数据导入、更新或维护）期间优化系统性能。

命令语法：

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

其中：

- `invalid` — 将索引器标记为过期，在下次cron运行时提示重新索引，除非它们被挂起。
- `suspended` — 暂时停止索引器的自动cron触发更新。 此状态同时适用于实时模式和计划模式，确保在密集型操作期间暂停自动更新。
- `valid` — 指示索引器数据是最新的，无需重新索引。
- `indexer` — 是索引器的空格分隔列表。 省略`indexer`以按相同方式配置所有索引器。

例如，要暂停特定的索引器，请输入：

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

示例结果：

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### 管理暂停的索引器状态

当索引器设置为`suspended`状态时，它主要影响自动重新索引和实例化视图更新。 下面是简要概述：

**已跳过重新索引**：系统跳过`suspended`索引器和共享同一`shared_index`的任何索引器的自动重新索引。 此方法通过避免重新索引与挂起进程相关的数据来节省系统资源。

**已跳过实例化视图更新**：与重新索引类似，系统还会暂停与`suspended`索引器或其共享索引相关的实例化视图的更新。 这种暂停进一步减少了暂停期间的系统负载。

>[!INFO]
>
>`indexer:reindex`命令对所有索引器（包括标记为`suspended`的索引器）进行重新索引，使其在自动索引器暂停时可用于手动更新。

>[!IMPORTANT]
>
>将索引器的状态从`valid`或`suspended`更改为`invalid`需要谨慎。 如果存在累积的未索引数据，此操作可能会导致性能下降。
>
>在手动将状态更新为`valid`以维护系统性能和数据完整性之前，确保所有数据都准确编制索引，这一点至关重要。
