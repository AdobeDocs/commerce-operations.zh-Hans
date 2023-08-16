---
title: 目录配置路径引用
description: 查看目录配置值的列表。
feature: Configuration, Catalogs
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---

# 目录配置路径引用

此部分列出了“管理员”中选项可用的变量名称和配置路径，位于 **商店** >设置> **配置** > **目录**.

此 [`magento app:config:dump` 命令](../cli/export-configuration.md) 将这些值写入共享配置文件， `app/etc/config.php`，它应该在源代码控制中。 要选择性地覆盖任何配置设置或设置敏感设置，请参阅 [使用环境变量覆盖配置设置](override-config-settings.md#environment-variables). 此主题可以 _非_ 列表 [敏感值和系统特定的值](config-reference-sens.md).

## 目录路径

这些配置值在管理员的以下位置提供： **商店** >设置> **配置** > **目录** > **目录**.

| 名称 | 配置路径 | 仅限商务？ |
|--------------|--------------|--------------|
| SKU蒙版 | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 元标题的蒙版 | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 元关键字的掩码 | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 元说明的蒙版 | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 列表模式 | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 网格上每页的产品允许值 | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 网格上每页的产品默认值 | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 每页产品数列表，允许值 | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 列表默认每页产品数 | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 产品列表排序方式 | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许每页所有产品 | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用平面目录类别 | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用平面目录产品 | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 每个产品的色板 | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许来宾编写评论 | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 产品价格变动时允许提醒 | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 价格警报电子邮件模板 | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 当产品重新上架时允许警报 | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stock警报电子邮件模板 | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 警报电子邮件发件人 | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 频率 | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 开始时间 | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 错误电子邮件发件人 | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 错误电子邮件模板 | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 为当前显示 | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认最近查看的产品计数 | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近比较的默认产品计数 | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Autostart基本视频 | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示相关视频 | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动重新启动视频 | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目录价格范围 | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认产品价格 | `catalog/price/default_product_price` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 显示产品计数 | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 价格导航步骤计算 | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认价格导航步骤 | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将价格间隔显示为一个价格 | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大价格间隔数 | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 区间除法限制 | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大深度 | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小查询长度 | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大查询长度 | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 搜索引擎 | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solr服务器超时 | `catalog/search/solr_server_timeout` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 索引模式 | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用搜索建议 | `catalog/search/search_suggestion_enabled` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 搜索建议计数 | `catalog/search/search_suggestion_count` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 显示每个建议的结果计数 | `catalog/search/search_suggestion_count_results_enabled` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 启用搜索Recommendations | `catalog/search/search_recommendations_enabled` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 搜索Recommendations计数 | `catalog/search/search_recommendations_count` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 显示每个推荐的结果计数 | `catalog/search/search_recommendations_count_results_enabled` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 要匹配的最少搜索词 | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生成“类别/产品”URL重写 | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 常用搜索词 | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 产品URL后缀 | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 类别URL后缀 | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将类别路径用于产品URL | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果URL键发生更改，请为URL创建永久重定向 | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 页面标题分隔符 | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 对类别使用规范链接元标记 | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 对产品使用规范链接Meta标记 | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用 | `catalog/magento_catalogpermissions/enabled` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 允许浏览类别 | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 客户组 | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 登陆页面 | `catalog/magento_catalogpermissions/restricted_landing_page` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 显示产品价格 | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 客户组 | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 允许添加到购物车 | `catalog/magento_catalogpermissions/grant_checkout_items` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 客户组 | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 不允许目录搜索依据 | `catalog/magento_catalogpermissions/deny_catalog_search` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 订单项目状态以启用下载 | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认最大下载次数 | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可共享 | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认示例标题 | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认链接标题 | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在新窗口中打开链接 | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用内容处置 | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果购物车包含可下载的项目，则禁用访客签出 | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用JavaScript日历 | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 日期字段顺序 | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 时间格式 | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 年份范围 | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用目录事件功能 | `catalog/magento_catalogevent/enabled` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 在Storefront上启用目录事件构件 | `catalog/magento_catalogevent/lister_output` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 要在事件滑块构件中显示的事件数 | `catalog/magento_catalogevent/lister_widget_limit` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 事件滑块构件中每次点击滚动的事件 | `catalog/magento_catalogevent/lister_widget_scroll` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 相关产品列表中的最大产品数 | `catalog/magento_targetrule/related_position_limit` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 显示相关产品 | `catalog/magento_targetrule/related_position_behavior` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 相关产品列表中的产品的旋转模式 | `catalog/magento_targetrule/related_rotation_mode` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 交叉销售产品列表中的最大产品数 | `catalog/magento_targetrule/crosssell_position_limit` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 显示交叉销售产品 | `catalog/magento_targetrule/crosssell_position_behavior` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 交叉销售产品列表中的产品的旋转模式 | `catalog/magento_targetrule/crosssell_rotation_mode` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 追加销售产品列表中的最大产品数 | `catalog/magento_targetrule/upsell_position_limit` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 显示追加销售产品 | `catalog/magento_targetrule/upsell_position_behavior` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 追加销售产品列表中的产品的旋转模式 | `catalog/magento_targetrule/upsell_rotation_mode` | ![仅商务](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 清单路径

这些配置值在管理员的以下位置提供： **商店** >设置> **配置** > **目录** > **库存**.

| 名称 | 配置路径 | 仅限商务？ |
|--------------|--------------|--------------|
| 下订单时减少库存 | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在取消订单时将物料的状态设置为有库存 | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示缺货产品 | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 仅X左侧阈值 | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在Storefront上以库存显示产品可用性 | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 与目录同步 | `cataloginventory/options/synchronize_with_catalog` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 管理库存 | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 延期交货 | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用延期库存更新 | `cataloginventory/item_options/use_deferred_stock_update` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 购物车中允许的最大数量 | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 缺货阈值 | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 购物车中允许的最小数量 | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 通知以下数量 | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用数量增量 | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 数量增量 | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动将贷项通知单项目返回至库存 | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 异步运行 | `cataloginventory/bulk_operations/async` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 异步批次大小 | `cataloginventory/bulk_operations/batch_size` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 提供商 | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计算模式 | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 值 | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 可视化促销路径

这些配置值在管理员的以下位置提供： **商店** >设置> **配置** > **目录** > **Visual Merchandiser**.

| 名称 | 配置路径 | 仅限商务？ |
|--------------|--------------|--------------|
| 类别规则的可见属性 | `visualmerchandiser/options/smart_attributes` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 最小库存阈值 | `visualmerchandiser/options/minimum_stock_threshold` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 颜色属性代码 | `visualmerchandiser/options/color_attribute_code` | ![仅商务](/help/assets/configuration/cloud-ee.png) |
| 颜色顺序 | `visualmerchandiser/options/color_order` | ![仅商务](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## XML站点地图路径

这些配置值在管理员的以下位置提供： **商店** >设置> **配置** > **目录** > **XML站点地图**.

| 名称 | 配置路径 | 仅限商务？ |
|--------------|--------------|--------------|
| 频率 | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 优先级 | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 频率 | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 优先级 | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将图像添加到站点地图 | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 频率 | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 优先级 | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 开始时间 | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 频率 | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 错误电子邮件发件人 | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 错误电子邮件模板 | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 每个文件的最大URL数 | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大文件大小 | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用提交到Robots.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## RSS馈送路径

这些配置值在管理员的以下位置提供： **商店** >设置> **配置** > **目录** > **RSS源**.

| 名称 | 配置路径 | 仅限商务？ |
|--------------|--------------|--------------|
| 启用RSS | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用RSS | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新产品 | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特殊产品 | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 优惠券/折扣 | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顶级类别 | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 客户订单状态通知 | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 通过电子邮件发送给朋友的路径

这些配置值在管理员的以下位置提供： **商店** >设置> **配置** > **目录** > **通过电子邮件发送给朋友**.

| 名称 | 配置路径 | 仅限商务？ |
|--------------|--------------|--------------|
| 已启用 | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 选择电子邮件模板 | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许来宾 | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大收件人数 | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 1小时内发送的最大产品数 | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 限制发送者 | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
