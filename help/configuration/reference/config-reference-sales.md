---
title: 销售配置路径参考
description: 请参阅销售配置值列表。
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '1500'
ht-degree: 0%

---


# 销售配置路径参考

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **销售**.

的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 将这些值写入共享配置文件， `app/etc/config.php`，它应位于源代码管理中。 要选择覆盖任何配置设置或设置敏感设置，请参阅 [使用环境变量覆盖配置设置](override-config-settings.md#environment-variables). 本主题包含 _not_ 列表 [敏感值和系统特定值](config-reference-sens.md).

## 销售路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **销售**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 隐藏客户IP | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小计 | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 折扣 | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 装运 | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税 | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 固定产品税 | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 总计 | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 礼品卡 | `sales/totals_sort/giftcardaccount` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 存储点数 | `sales/totals_sort/customerbalance` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 允许重新排序 | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF打印输出(200x50)的徽标 | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML打印视图的徽标 | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 地址 | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用 | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小金额 | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包括税额 | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 描述消息 | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 购物车中显示错误 | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在多地址结账中单独验证每个地址 | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 多地址描述消息 | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 购物车中显示的多地址错误 | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用聚合数据 | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 待定付款订单生命周期（分钟） | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许按订单级别发送礼品邮件 | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许订购物品的礼品邮件 | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许在订单级别包装礼品 | `sales/gift_options/wrapping_allow_order` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 允许订单物料的礼品包装 | `sales/gift_options/wrapping_allow_items` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 允许礼品收据 | `sales/gift_options/allow_gift_receipt` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 允许打印卡 | `sales/gift_options/allow_printed_card` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 打印卡的默认价格 | `sales/gift_options/printed_card_price` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 启用MAP | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示实际价格 | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认弹出文本消息 | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认“What&#39;s This”文本消息 | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在Storefront中对我的帐户启用按SKU排序 | `sales/product_sku/my_account_enable` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 按钮文本 | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 客户群组 | `sales/product_sku/allowed_groups` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 启用存档 | `sales/magento_salesarchive/active` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 存档已购买的订单 | `sales/magento_salesarchive/age` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 要存档的订单状态 | `sales/magento_salesarchive/order_statuses` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 在店面上启用RMA | `sales/magento_rma/enabled` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 在产品级别启用RMA | `sales/magento_rma/enabled_on_product` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 使用存储地址 | `sales/magento_rma/use_store_address` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## 销售电子邮件路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **销售电子邮件**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 异步发送 | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单确认电子邮件发件人 | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单确认模板 | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新的来宾订单确认模板 | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送订单电子邮件复制方法 | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 订单评论电子邮件发件人 | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 订单评论电子邮件模板 | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 为来宾订购评论电子邮件模板 | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送订单评论电子邮件复制方法 | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发票电子邮件发件人 | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发票电子邮件模板 | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来宾的发票电子邮件模板 | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送发票电子邮件复制方法 | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发票评论电子邮件发件人 | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发票评论电子邮件模板 | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来宾的发票评论电子邮件模板 | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送发票备注电子邮件复制方法 | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运电子邮件发件人 | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运电子邮件模板 | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来宾的发运电子邮件模板 | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送发运电子邮件复制方法 | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运评论电子邮件发件人 | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运评论电子邮件模板 | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来宾的发运评论电子邮件模板 | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送发运评论电子邮件复制方法 | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 贷项通知单电子邮件发件人 | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 贷项通知单电子邮件模板 | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来宾的贷项通知单电子邮件模板 | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送贷项通知单电子邮件复制方法 | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 贷项通知单评论电子邮件发件人 | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 贷项通知单评论电子邮件模板 | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来宾的贷项通知单评论电子邮件模板 | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送贷项通知单评论电子邮件复制方法 | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `sales_email/magento_rma/enabled` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| RMA电子邮件发送者 | `sales_email/magento_rma/identity` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| RMA电子邮件模板 | `sales_email/magento_rma/template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 来宾的RMA电子邮件模板 | `sales_email/magento_rma/guest_template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 发送RMA电子邮件复制方法 | `sales_email/magento_rma/copy_method` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `sales_email/magento_rma_auth/enabled` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| RMA授权电子邮件发件人 | `sales_email/magento_rma_auth/identity` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| RMA授权电子邮件模板 | `sales_email/magento_rma_auth/template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 来宾的RMA授权电子邮件模板 | `sales_email/magento_rma_auth/guest_template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 发送RMA授权电子邮件复制方法 | `sales_email/magento_rma_auth/copy_method` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `sales_email/magento_rma_comment/enabled` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| RMA评论电子邮件发件人 | `sales_email/magento_rma_comment/identity` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| RMA评论电子邮件模板 | `sales_email/magento_rma_comment/template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 来宾的RMA评论电子邮件模板 | `sales_email/magento_rma_comment/guest_template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 发送RMA电子邮件复制方法 | `sales_email/magento_rma_comment/copy_method` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `sales_email/magento_rma_customer_comment/enabled` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| RMA评论电子邮件发件人 | `sales_email/magento_rma_customer_comment/identity` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| RMA评论电子邮件收件人 | `sales_email/magento_rma_customer_comment/recipient` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| RMA评论电子邮件模板 | `sales_email/magento_rma_customer_comment/template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 发送RMA电子邮件复制方法 | `sales_email/magento_rma_customer_comment/copy_method` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 在标题中显示订单ID | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在标题中显示订单ID | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在标题中显示订单ID | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 税种路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **税**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 装运的税种 | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 礼品选项的税种 | `tax/classes/wrapping_tax_class` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 产品的默认税种 | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 客户的默认税种 | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 基于的计税方法 | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计税依据 | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目录价格 | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 运费 | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 应用客户税 | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 对价格应用折扣 | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税应纳 | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用跨境贸易 | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认国家/地区 | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认状态 | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认帖子代码 | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在目录中显示产品价格 | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示装运价格 | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示价格 | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示小计 | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示发运金额 | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示礼品包装价格 | `tax/cart_display/gift_wrapping` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 显示打印卡的价格 | `tax/cart_display/printed_card` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 在订单中包括税 | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示完整税汇总 | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示零税小计 | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示价格 | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示小计 | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示发运金额 | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示礼品包装价格 | `tax/sales_display/gift_wrapping` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 显示打印卡的价格 | `tax/sales_display/printed_card` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 在订单中包括税 | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示完整税汇总 | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示零税小计 | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用FPT | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在产品列表中显示价格 | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在“产品查看”页面上显示价格 | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在销售模块中显示价格 | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在电子邮件中显示价格 | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 对FPT应用税 | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在小计中包括FPT | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 结帐路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **结帐**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 启用Onepage Checkout | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许来宾结帐 | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示帐单地址开启 | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用条款和条件 | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 报价存留期（天） | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将产品重定向添加到购物车后 | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 分组的产品图像 | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可配置产品映像 | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 预览报价生命周期（分钟） | `checkout/cart/preview_quota_lifetime` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 显示购物车摘要 | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示购物车侧栏 | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近添加的最大显示项目数 | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款失败的电子邮件发件人 | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款失败的电子邮件接收器 | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款失败模板 | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送付款失败的电子邮件复制方法 | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 装运设置路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **装运设置**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 应用自定义装运策略 | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 装运政策 | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 多传送设置路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **多传送设置**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 允许将邮运到多个地址 | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许发运至多个地址的最大数量 | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 投放方法路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **投放方法**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 已启用 | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 方法名称 | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 类型 | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 价格 | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计算处理费用 | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手续费 | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示的错误消息 | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至适用国家/地区 | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至特定国家/地区 | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示方法（如果不适用） | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 方法名称 | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最低订单金额 | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示的错误消息 | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至适用国家/地区 | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至特定国家/地区 | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示方法（如果不适用） | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 方法名称 | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 条件 | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在价格计算中包含虚拟产品 | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 导出 | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 导入 | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计算处理费用 | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手续费 | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示的错误消息 | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至适用国家/地区 | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至特定国家/地区 | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示方法（如果不适用） | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用结帐功能 | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 为RMA启用 | `carriers/ups/active_rma` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| UPS类型 | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 模式 | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 装运的来源 | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 网关URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用协议费率 | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包请求类型 | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 容器 | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 权重单位 | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目标类型 | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大包装重量（请咨询您的运输承运人，了解最大受支持的运输重量） | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拾取方法 | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小包装重量（请咨询您的运输承运人，以获得最小支持的运输重量） | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计算处理费用 | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已应用处理 | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手续费 | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许的方法 | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用免费装运阈值 | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免运费金额阈值 | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示的错误消息 | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至适用国家/地区 | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至特定国家/地区 | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示方法（如果不适用） | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用结帐功能 | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 为RMA启用 | `carriers/usps/active_rma` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 模式 | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包请求类型 | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 容器 | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 长度 | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 宽度 | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高度 | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 吉尔特 | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可加工 | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大包装重量（请咨询您的运输承运人，了解最大受支持的运输重量） | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计算处理费用 | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已应用处理 | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手续费 | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许的方法 | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用免费装运阈值 | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免运费金额阈值 | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示的错误消息 | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至适用国家/地区 | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至特定国家/地区 | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示方法（如果不适用） | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用结帐功能 | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 为RMA启用 | `carriers/fedex/active_rma` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 标题 | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web服务URL（生产） | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web服务URL（沙盒） | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包请求类型 | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包装 | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 德罗波夫 | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 权重单位 | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大包装重量（请咨询您的运输承运人，了解最大受支持的运输重量） | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计算处理费用 | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已应用处理 | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手续费 | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 住宅交付 | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许的方法 | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 中心ID | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用免费装运阈值 | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免运费金额阈值 | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示的错误消息 | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至适用国家/地区 | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至特定国家/地区 | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示方法（如果不适用） | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用结帐功能 | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 为RMA启用 | `carriers/dhl/active_rma` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 标题 | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 内容类型 | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计算处理费用 | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已应用处理 | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手续费 | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 划分顺序权重 | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 权重单位 | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高度 | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 深度 | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 宽度 | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许的方法 | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许的方法 | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 准备时间 | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示的错误消息 | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用免费装运阈值 | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免运费金额阈值 | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至适用国家/地区 | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发运至特定国家/地区 | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示方法（如果不适用） | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Google API路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **Google API**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 启用 | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 帐户类型 | `google/analytics/type` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 启用内容实验 | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目录页面的列表属性 | `google/analytics/catalog_page_list_value` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 交叉销售块的列表属性 | `google/analytics/crosssell_block_list_value` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 向上销售块的列表属性 | `google/analytics/upsell_block_list_value` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 相关产品块的列表属性 | `google/analytics/related_block_list_value` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 搜索结果页面的列表属性 | `google/analytics/search_page_list_value` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 促销活动字段“标签”的“内部促销活动”。 | `google/analytics/promotions_list_value` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 启用 | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转化ID | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转换语言 | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转换格式 | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转换颜色 | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转化标签 | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转化值类型 | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转化值 | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 礼品卡路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **礼品卡**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 礼品卡通知电子邮件发送者 | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 礼品卡通知电子邮件模板 | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可赎回 | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 存留期（天） | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许礼品消息 | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 礼品消息最大长度 | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在订单物料为 | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 礼品卡电子邮件发送者 | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 礼品卡模板 | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代码长度 | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代码格式 | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代码前缀 | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代码后缀 | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将每X个字符划线 | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新池大小 | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 低代码池阈值 | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
