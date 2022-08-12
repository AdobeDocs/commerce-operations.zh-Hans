---
title: “ [!UICONTROL Indexing] 选项卡”
description: 了解 [!UICONTROL Indexing] 选项卡 [!DNL Observation for Adobe Commerce].
source-git-commit: 1f334f329b72b715afa7f3617b1ce2fb8004f816
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# 的 [!UICONTROL Indexing] 选项卡

的 **[!UICONTROL Indexing]** 选项卡尝试解释索引问题并确定潜在原因。

## [!UICONTROL Core index invalidated]

![核心指数失效](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

的 **[!UICONTROL Core index invalidated]** 框架会查看在选定的时间范围内的索引失效情况。 如果与其他资源密集型cron同时进行索引，则会给站点资源带来沉重的负载。

* “%目录产品规则索引器已失效%”)作为“catalog_product_rule_idx_reset”
* “%目录规则产品索引器已失效%”)作为“catalog_rule_product_idx_reset”
* “%目录搜索索引器已失效%”)作为“catalog_search_idx_reset”
* “%类别产品索引器已失效%”)作为“category_products_idx_reset”
* “%Customer Grid索引器已失效%”)作为“customer_grid_idx_reset”
* “%设计配置网格索引器已失效%”)作为“design_config_grid_idx_
* “%产品类别索引器已失效%”)作为“product_categories_idx_reset”
* “%Product EAV索引器已失效%”)作为“product_eav_idx_reset”
* “%产品价格索引器已失效%”)作为“product_price_idx_reset”
* “%Stock索引器已失效%”)作为“stock_idx_reset”
* “%库存索引器已失效%”)作为“inventory_idx_reset”
* “%库存索引器已失效%”)作为“inventory_idx_reset”
* “%销售规则索引器已失效%”)作为“sales_rule_idx_reset”

## [!UICONTROL Core index rebuilds]

![核心索引重建](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

的 **[!UICONTROL Core index rebuilds]** 框架会查看选定时间范围内的核心索引重新构建。 以下是从日志中解析的字符串，以指示索引重建完成。

* “%目录产品规则索引已重建%”)作为“catalog_product_rule_idx”
* “%目录规则产品索引已重建%”)作为“catalog_rule_product_idx”
* “%目录搜索索引已重建%”)为“catalog_search_idx”
* “%类别产品索引已成功重建%”)作为“category_products_idx”
* “%客户网格索引已重建%”)为“customer_grid_idx”
* “%设计配置网格索引已重建%”)作为“design_config_grid_idx”
* “%产品类别索引已重建%”)为“product_categories_idx”
* “%Product EAV索引已重建%”)作为“product_eav_idx”
* “%产品价格指数已重建%”)作为“product_price_idx”
* “%股指已重建%”)为“stock_idx”
* “%库存索引已成功重建%”)作为“inventory_idx”
* %Product/Target规则索引已成功重建%&#39;)作为&#39;prod_target_rule_idx&#39;
* “%已成功重建销售规则索引%”)作为“sales_rule_idx”


## [!UICONTROL catalogsearch index table(s)]

![目录搜索索引表](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

的 **[!UICONTROL catalogsearch index table(s)]** 框架会查看选定时间范围内的目录搜索索引表。 此查询正在查看对表名中具有“%catalogsearch%”的表执行任何数据存储操作的持续时间。

## [!UICONTROL product index table(s)]

![产品索引表](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

的 **[!UICONTROL product index table(s)]** frame会查看选定时间范围内的产品索引表。 此查询正在查看对表名中具有“%product%”的表执行任何数据存储操作的持续时间。
