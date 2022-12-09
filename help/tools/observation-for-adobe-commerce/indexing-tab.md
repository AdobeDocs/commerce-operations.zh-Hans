---
title: “ [!UICONTROL Indexing] 选项卡”
description: 了解 [!UICONTROL Indexing] 选项卡 [!DNL Observation for Adobe Commerce].
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 的 [!UICONTROL Indexing] 选项卡

的 **[!UICONTROL Indexing]** 选项卡尝试解释索引问题并确定潜在原因。

## [!UICONTROL Core index invalidated]

![核心指数失效](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

的 **[!UICONTROL Core index invalidated]** 框架会查看在选定的时间范围内的索引失效情况。 如果正在与其他资源密集型活动同时进行索引 [!DNL crons]，则会对网站资源造成沉重负载。

* `%Catalog Product Rule indexer has been invalidated%`)作为 `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`)作为 `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`)作为 `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`)作为 `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`)作为 `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`)作为 `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`)作为 `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`)作为 `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`)作为 `product_price_idx_reset`
* `%Stock indexer has been invalidated%`)作为 `stock_idx_reset`
* `%Inventory indexer has been invalidated%`)作为 `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`)作为 `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`)作为 `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![核心索引重建](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

的 **[!UICONTROL Core index rebuilds]** 框架会查看选定时间范围内的核心索引重新构建。 以下是从日志中解析的字符串，以指示索引重建完成。

* `%Catalog Product Rule index has been rebuilt%`)作为 `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`)作为 `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`)作为 `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`)作为 `category_products_idx`
* `%Customer Grid index has been rebuilt%`)作为 `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`)作为 `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`)作为 `product_categories_idx`
* `%Product EAV index has been rebuilt%`)作为 `product_eav_idx`
* `%Product Price index has been rebuilt%`)作为 `product_price_idx`
* `%Stock index has been rebuilt%`)作为 `stock_idx`
* `%Inventory index has been rebuilt successfully%`)作为 `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`)作为 `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`)作为 `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![目录搜索索引表](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

的 **[!UICONTROL catalogsearch index table(s)]** 框架会查看选定时间范围内的目录搜索索引表。 此查询正在查看针对具有的表执行任何数据存储操作的持续时间 `%catalogsearch%` 中。

## [!UICONTROL product index table(s)]

![产品索引表](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

的 **[!UICONTROL product index table(s)]** frame会查看选定时间范围内的产品索引表。 此查询正在查看针对具有的表执行任何数据存储操作的持续时间 `%product%` 中。
