---
title: 此 [!UICONTROL Indexing] 標籤
description: 瞭解 [!UICONTROL Indexing] 索引標籤/ [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 此 [!UICONTROL Indexing] 標籤

此 **[!UICONTROL Indexing]** Tab會嘗試解釋索引化問題，並找出可能的原因。

## [!UICONTROL Core index invalidated]

![核心索引已失效](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

此 **[!UICONTROL Core index invalidated]** 框架會檢視所選時間範圍內的索引失效。 如果索引與其他資源密集型同時發生 [!DNL crons]，會對網站資源造成大量負載。

* `%Catalog Product Rule indexer has been invalidated%`)作為 `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`)作為 `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`)作為 `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`)作為 `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`)作為 `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`)作為 `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`)作為 `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`)作為 `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`)作為 `product_price_idx_reset`
* `%Stock indexer has been invalidated%`)作為 `stock_idx_reset`
* `%Inventory indexer has been invalidated%`)作為 `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`)作為 `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`)作為 `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![核心索引重建](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

此 **[!UICONTROL Core index rebuilds]** frame會檢視在選取的時間範圍內重建核心索引。 以下是從記錄中剖析的字串，用以指出索引重建完成。

* `%Catalog Product Rule index has been rebuilt%`)作為 `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`)作為 `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`)作為 `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`)作為 `category_products_idx`
* `%Customer Grid index has been rebuilt%`)作為 `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`)作為 `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`)作為 `product_categories_idx`
* `%Product EAV index has been rebuilt%`)作為 `product_eav_idx`
* `%Product Price index has been rebuilt%`)作為 `product_price_idx`
* `%Stock index has been rebuilt%`)作為 `stock_idx`
* `%Inventory index has been rebuilt successfully%`)作為 `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`)作為 `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`)作為 `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![catalogsearch索引表格](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

此 **[!UICONTROL catalogsearch index table(s)]** frame會在選取的時間範圍內檢視catalogsearch索引表格。 此查詢會檢視針對具有下列專案的資料表的任何資料存放區作業的持續時間： `%catalogsearch%` 在表格名稱中。

## [!UICONTROL product index table(s)]

![產品索引表格](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

此 **[!UICONTROL product index table(s)]** frame會檢視所選時間範圍內的產品索引表格。 此查詢會檢視針對具有下列專案的資料表的任何資料存放區作業的持續時間： `%product%` 在表格名稱中。
