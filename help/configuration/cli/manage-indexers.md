---
title: 管理索引器
description: 請參閱如何檢視和管理Commerce索引器的範例。
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 795d4e9d1910d0ad826eb6c82ac451ac58e43063
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 0%

---

# 管理索引器

{{file-system-owner}}

若要檢視所有索引器的清單：

```bash
bin/magento indexer:info
```

清單顯示如下：

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
> 使用「即時搜尋」、「目錄服務」或「產品Recommendations」的Adobe Commerce商家可以選擇使用 [以SaaS為基礎的價格索引](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## 檢視索引器狀態

使用此命令可檢視所有索引器或特定索引器的狀態。 例如，瞭解索引器是否需要重新索引。

命令選項：

```bash
bin/magento indexer:status [indexer]
```

位置 `[indexer]` 是以空格分隔的索引子清單。 省略 `[indexer]` 以檢視所有索引器的狀態。

範例結果：

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

使用此命令可只重新索引一次所有或選取的索引子。

>[!INFO]
>
>此命令只會重新索引一次。 若要讓索引子保持最新狀態，您必須設定 [cron工作](../cli/configure-cron-jobs.md).

命令選項：

```bash
bin/magento indexer:reindex [indexer]
```

位置 `[indexer]` 是以空格分隔的索引子清單。 省略 `[indexer]` 重新索引所有索引子。

範例結果：

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
>對於擁有大量產品、客戶、類別和促銷規則的商店，重新索引所有索引子可能需要很長時間。

### 以平行模式重新索引

索引器具有範圍和多執行緒，以支援在平行模式下重新索引。 它透過索引器的維度並行，並在多個執行緒上執行，以減少處理時間。

在此內容中， `dimension` 是重新索引的範圍，例如 `website` 或只是特定 `customer_group`.

索引平行化只會影響範圍的索引子，這表示Commerce會使用索引子作為其範圍將資料分割成多個表格，而不是將所有資料保留在一個表格中。

您可以在平行模式下執行下列索引：

- `Catalog Search Fulltext` 可透過商店檢視來並行處理。
- `Category Product` 可透過商店檢視來並行處理。
- `Catalog Price` 可依網站和客戶群組並行。
- `Catalog Permissions` 可依客戶群組並行。

>[!INFO]
>
>目錄搜尋全文檢索與類別產品的平行化預設為啟用。

若要使用平行化，請為產品價格索引器設定其中一個可用的維度模式：

- `none` （預設）
- `website`
- `customer_group`
- `website_and_customer_group`

例如，若要設定每個網站的模式：

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

若要對目錄許可權使用平行化，請為目錄許可權索引器設定其中一個可用的維度模式：

- `none` （預設）
- `customer_group`

或檢查目前模式：

```bash
bin/magento indexer:show-dimensions-mode
```

若要以平行模式重新索引，請使用環境變數執行reindex指令 `MAGE_INDEXER_THREADS_COUNT`，或將環境變數新增至 `env.php` 檔案。 此變數會設定重新索引處理的執行緒數目。

例如，下列命令會執行 `Catalog Search Fulltext` 跨三個執行緒的索引器：

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## 重設索引子

使用此命令可讓所有索引器或特定索引器的狀態失效。

命令選項：

```bash
bin/magento indexer:reset [indexer]
```

位置 ```[indexer]``` 是以空格分隔的索引子清單。 省略 `[indexer]` 讓所有索引子失效。

範例結果：

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

## 設定索引子

使用此命令設定下列索引子選項：

- **儲存時更新(`realtime`)**：在「管理員」中變更後，會更新索引資料。 （例如，將產品新增至管理員中的類別後，類別產品索引會重新索引。） 這是預設值。
- **依排程更新(`schedule`)**：資料會根據cron作業設定的排程建立索引。

[進一步瞭解索引](https://developer.adobe.com/commerce/php/development/components/indexing/).

### 顯示目前的設定

若要檢視目前的索引器組態：

```bash
bin/magento indexer:show-mode [indexer]
```

位置 `[indexer]` 是以空格分隔的索引子清單。 省略 `[indexer]` 以顯示所有索引子模式。 例如，若要顯示所有索引器的模式：

範例結果：

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

### 設定索引子

>[!INFO]
>
>在切換索引器模式之前，建議您先將網站放到 [維護](../../installation/tutorials/maintenance-mode.md) 模式和 [停用cron工作](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). 這可確保您不會遭受資料庫鎖定的困擾。

若要指定索引器組態：

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

其中：

- `realtime` — 將選取的索引子設定為在儲存時更新。
- `schedule` — 根據cron排程設定要儲存的指定索引子。
- `indexer` — 是以空格分隔的索引子清單。 省略 `indexer` 以相同方式設定所有索引子。

例如，若只要變更要依排程更新的類別產品和產品類別索引器，請輸入：

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

範例結果：

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

當索引器模式設定為時，會新增索引器相關的資料庫觸發程式 `schedule` 並在索引器模式設定為時移除 `realtime`. 如果索引子設定為時，資料庫中缺少觸發程式 `schedule`，將索引子變更為 `realtime` 然後變更回 `schedule`. 這會重設觸發程式。
