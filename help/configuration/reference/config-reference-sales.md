---
title: 銷售設定路徑參考
description: 檢視銷售組態值清單。
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---

# 銷售設定路徑參考

本節列出「管理」下方的選項可用的變數名稱和設定路徑。 **商店** >設定> **設定** > **銷售**.

此 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將這些值寫入共用組態檔， `app/etc/config.php`，這應該是在原始檔控制中。 若要選擇性地覆寫任何組態設定或設定敏感設定，請參閱 [使用環境變數來覆寫組態設定](override-config-settings.md#environment-variables). 此主題會 _not_ 清單 [敏感值和系統特定值](config-reference-sens.md).

## 銷售路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **銷售**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 隱藏客戶IP | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計 | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 折扣 | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨 | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 稅金 | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 固定產品稅金 | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 全部總計 | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禮品卡 | `sales/totals_sort/giftcardaccount` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 商店點數 | `sales/totals_sort/customerbalance` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許重新排序 | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF列印輸出的標誌(200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML列印檢視的標誌 | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 地址 | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用 | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小金額 | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包含稅捐至金額 | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 說明訊息 | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在購物車中顯示的錯誤 | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在多位址簽出中分別驗證每個位址 | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 多重位址說明訊息 | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 要在購物車中顯示的多重地址錯誤 | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用彙總資料 | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 暫緩付款訂單期限（分鐘） | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許訂單層級的贈品訊息 | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許訂單專案的贈品訊息 | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許在訂單層級使用贈品包裝 | `sales/gift_options/wrapping_allow_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許訂購專案的贈品包裝 | `sales/gift_options/wrapping_allow_items` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許贈品收據 | `sales/gift_options/allow_gift_receipt` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許列印卡片 | `sales/gift_options/allow_printed_card` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 列印卡片的預設價格 | `sales/gift_options/printed_card_price` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 啟用地圖 | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示實際價格 | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設快顯文字訊息 | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設「這是什麼」文字訊息 | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在Storefront的「我的帳戶」上啟用依SKU排序 | `sales/product_sku/my_account_enable` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 按鈕文字 | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 客戶群組 | `sales/product_sku/allowed_groups` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 啟用封存 | `sales/magento_salesarchive/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 封存購買訂單 | `sales/magento_salesarchive/age` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 要封存的訂單狀態 | `sales/magento_salesarchive/order_statuses` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 在店面啟用RMA | `sales/magento_rma/enabled` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 在產品層級啟用RMA | `sales/magento_rma/enabled_on_product` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 使用商店地址 | `sales/magento_rma/use_store_address` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 銷售電子郵件路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **銷售電子郵件**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 非同步傳送 | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單確認電子郵件寄件者 | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新增訂單確認範本 | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新增Guest訂單確認範本 | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送訂單電子郵件副本方法 | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 訂單評論電子郵件寄件者 | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 訂單評論電子郵件範本 | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 訪客的訂單評論電子郵件範本 | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送訂單註解電子郵件複製方法 | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發票電子郵件寄件者 | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發票電子郵件範本 | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的發票電子郵件範本 | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送發票電子郵件複製方法 | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 發票註解電子郵件寄件者 | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 商業發票註解電子郵件範本 | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的商業發票註解電子郵件範本 | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送商業發票註解電子郵件複製方法 | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出貨電子郵件寄件者 | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出貨電子郵件範本 | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 客人的出貨電子郵件範本 | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送出貨電子郵件複製方法 | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出貨評論電子郵件寄件者 | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出貨評論電子郵件範本 | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 客人的出貨評論電子郵件範本 | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送出貨備註電子郵件複製方法 | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 銷退折讓單電子郵件寄件者 | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 銷退折讓單電子郵件範本 | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的銷退折讓單電子郵件範本 | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送銷退折讓單電子郵件複製方法 | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 銷退折讓單備註電子郵件寄件者 | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 銷退折讓單備註電子郵件範本 | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來賓的銷退折讓單註解電子郵件範本 | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送銷退折讓單備註電子郵件複製方法 | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `sales_email/magento_rma/enabled` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| RMA電子郵件寄件者 | `sales_email/magento_rma/identity` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| RMA電子郵件範本 | `sales_email/magento_rma/template` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來賓的RMA電子郵件範本 | `sales_email/magento_rma/guest_template` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 傳送RMA電子郵件複製方法 | `sales_email/magento_rma/copy_method` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `sales_email/magento_rma_auth/enabled` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| RMA授權電子郵件寄件者 | `sales_email/magento_rma_auth/identity` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| RMA授權電子郵件範本 | `sales_email/magento_rma_auth/template` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來賓的RMA授權電子郵件範本 | `sales_email/magento_rma_auth/guest_template` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 傳送RMA授權電子郵件複製方法 | `sales_email/magento_rma_auth/copy_method` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `sales_email/magento_rma_comment/enabled` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| RMA註解電子郵件寄件者 | `sales_email/magento_rma_comment/identity` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| RMA註解電子郵件範本 | `sales_email/magento_rma_comment/template` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來賓的RMA註解電子郵件範本 | `sales_email/magento_rma_comment/guest_template` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 傳送RMA電子郵件複製方法 | `sales_email/magento_rma_comment/copy_method` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `sales_email/magento_rma_customer_comment/enabled` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| RMA註解電子郵件寄件者 | `sales_email/magento_rma_customer_comment/identity` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| RMA註解電子郵件收件者 | `sales_email/magento_rma_customer_comment/recipient` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| RMA註解電子郵件範本 | `sales_email/magento_rma_customer_comment/template` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 傳送RMA電子郵件複製方法 | `sales_email/magento_rma_customer_comment/copy_method` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 在頁首中顯示訂單ID | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在頁首中顯示訂單ID | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在頁首中顯示訂單ID | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 稅捐路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **稅金**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 出貨的稅捐類別 | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 贈品選項的稅捐類別 | `tax/classes/wrapping_tax_class` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 產品的預設稅捐類別 | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 客戶的預設稅捐類別 | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 稅捐計算方式依據 | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 稅捐計算依據 | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目錄價格 | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨價格 | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 套用客戶稅金 | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 套用價格折扣 | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 套用稅金於 | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用跨境貿易 | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設國家 | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設狀態 | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設郵遞區號 | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在目錄中顯示產品價格 | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示送貨價格 | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示價格 | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示小計 | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示運費金額 | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示贈品包裝價格 | `tax/cart_display/gift_wrapping` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 顯示列印的卡片價格 | `tax/cart_display/printed_card` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 包含訂單總金額中的稅捐 | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示完整稅捐彙總 | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示零稅捐小計 | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示價格 | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示小計 | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示運費金額 | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示贈品包裝價格 | `tax/sales_display/gift_wrapping` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 顯示列印的卡片價格 | `tax/sales_display/printed_card` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 包含訂單總金額中的稅捐 | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示完整稅捐彙總 | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示零稅捐小計 | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用FPT | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在產品清單中顯示價格 | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在產品檢視頁面上顯示價格 | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在銷售模組中顯示價格 | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在電子郵件中顯示價格 | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將稅金套用至FPT | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在小計中包含FPT | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 簽出路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **簽出**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 啟用Onepage Checkout | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許訪客結帳 | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示帳單地址於 | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用條款與條件 | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 報價存留期（天） | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新增產品後，重新導向至購物車 | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 群組的產品影像 | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可設定的產品影像 | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預覽報價存留期（分鐘） | `checkout/cart/preview_quota_lifetime` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 顯示購物車摘要 | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示購物車側欄 | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大顯示最近新增的專案 | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款失敗的電子郵件寄件者 | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款失敗的電子郵件接收者 | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款失敗的範本 | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送付款失敗的電子郵件複製方法 | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 送貨設定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **送貨設定**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 套用自訂送貨原則 | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨原則 | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 多送貨設定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **多送貨設定**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 允許運送至多個地址 | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許運送至多個地址的最大數量 | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 傳遞方法路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **傳遞方法**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 已啟用 | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 方法名稱 | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 型別 | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 價格 | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤訊息 | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至適用國家/地區 | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至特定國家/地區 | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示方法（如果不適用） | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 方法名稱 | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購金額 | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤訊息 | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至適用國家/地區 | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至特定國家/地區 | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示方法（如果不適用） | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 方法名稱 | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 條件 | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將虛擬產品納入價格計算 | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 匯出 | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 匯入 | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤訊息 | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至適用國家/地區 | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至特定國家/地區 | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示方法（如果不適用） | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用以結帳 | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用RMA | `carriers/ups/active_rma` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| UPS型別 | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 模式 | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出貨來源 | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 閘道URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用議價匯率 | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 套件要求型別 | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 容器 | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重量單位 | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目的地型別 | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大包裹重量（請洽詢您的貨運業者，瞭解支援的最大貨運重量） | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 取車方法 | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包裝重量下限（請洽詢您的運送公司，瞭解支援的最低運送重量） | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 處理已套用 | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的方法 | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用免費送貨閾值 | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免運費金額臨界值 | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤訊息 | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至適用國家/地區 | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至特定國家/地區 | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示方法（如果不適用） | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用以結帳 | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用RMA | `carriers/usps/active_rma` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 模式 | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 套件要求型別 | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 容器 | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 長度 | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 寬度 | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高度 | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 周長 | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可加工 | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大包裹重量（請洽詢您的貨運業者，瞭解支援的最大貨運重量） | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 處理已套用 | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的方法 | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用免費送貨閾值 | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免運費金額臨界值 | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤訊息 | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至適用國家/地區 | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至特定國家/地區 | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示方法（如果不適用） | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用以結帳 | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用RMA | `carriers/fedex/active_rma` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web服務URL （生產） | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web服務URL （沙盒） | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 套件要求型別 | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 封裝 | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 流失 | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重量單位 | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大包裹重量（請洽詢您的貨運業者，瞭解支援的最大貨運重量） | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 處理已套用 | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 住宅配送 | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的方法 | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 中心ID | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用免費送貨閾值 | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免運費金額臨界值 | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤訊息 | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至適用國家/地區 | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至特定國家/地區 | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示方法（如果不適用） | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用以結帳 | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用RMA | `carriers/dhl/active_rma` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 內容型別 | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算手續費 | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 處理已套用 | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手續費 | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 除序權數 | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重量單位 | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高度 | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 深度 | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 寬度 | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的方法 | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的方法 | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 準備時間 | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示的錯誤訊息 | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用免費送貨閾值 | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 免運費金額臨界值 | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至適用國家/地區 | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送貨至特定國家/地區 | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示方法（如果不適用） | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Google API路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **GOOGLE API**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 啟用 | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 帳戶型別 | `google/analytics/type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 啟用內容實驗 | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目錄頁面的清單屬性 | `google/analytics/catalog_page_list_value` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 交叉銷售區塊的清單屬性 | `google/analytics/crosssell_block_list_value` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 向上銷售區塊的清單屬性 | `google/analytics/upsell_block_list_value` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 相關產品區塊的清單屬性 | `google/analytics/related_block_list_value` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 搜尋結果頁面的清單屬性 | `google/analytics/search_page_list_value` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 「標籤」欄位的「內部促銷」。 | `google/analytics/promotions_list_value` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 啟用 | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換ID | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換語言 | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換格式 | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換色彩 | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換標籤 | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換值型別 | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉換值 | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 禮品卡路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **禮品卡**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 禮品卡通知電子郵件寄件者 | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禮品卡通知電子郵件範本 | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 可贖回 | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 期限（天） | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許贈品訊息 | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 贈品訊息最大長度 | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 當訂單料號為時，產生禮品卡帳戶 | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禮品卡電子郵件寄件者 | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禮品卡範本 | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 程式碼長度 | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 程式碼格式 | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 程式碼首碼 | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 程式碼尾碼 | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將每X個字元加上破折號 | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新集區大小 | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 低程式碼集區臨界值 | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
