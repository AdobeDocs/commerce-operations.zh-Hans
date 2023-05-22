---
title: 付款設定路徑參考
description: 檢視可設定的付款方式值清單。
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '4100'
ht-degree: 0%

---

# 付款設定路徑參考

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **付款方法**.

此 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將這些值寫入共用組態檔， `app/etc/config.php`，這應該是在原始檔控制中。 若要選擇性地覆寫任何組態設定或設定敏感設定，請參閱 [使用環境變數來覆寫組態設定](override-config-settings.md#environment-variables). 此主題會 _not_ 清單 [敏感值和系統特定值](config-reference-sens.md).

這些設定會依付款方式進一步組織。

## PayPal路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| 啟用此解決方案 | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用In-Context簽出體驗 | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用PayPal點數 | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用PayPal點數 | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示 | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示 | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示 | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示 | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示在產品詳細資訊頁面上 | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在購物車上顯示 | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款適用來源 | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用國家/地區付款自 | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用SSL驗證 | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉移購物車明細專案 | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 略過訂單複查步驟 | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉移購物車明細專案 | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 移轉送貨選項 | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 捷徑按鈕風格 | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用PayPal來賓結帳 | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要客戶的帳單地址 | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 帳單協定註冊 | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款適用來源 | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用國家/地區付款自 | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用SSL驗證 | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 轉移購物車明細專案 | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在帳單協定精靈中允許 | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用自動擷取 | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程 | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 時間 | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal產品標誌 | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頁面樣式 | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頁首影像URL | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頁首背景色彩 | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頁首邊框色彩 | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頁面背景顏色 | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用此解決方案 | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序PayPal信用 | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示在產品詳細資訊頁面上 | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 授權執行期間（天） | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 訂單有效期間（天） | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 子授權數量 | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在購物車上顯示 | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款適用來源 | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用國家/地區付款自 | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用SSL驗證 | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payments Pro

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| API驗證方法 | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| API使用Proxy | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Payments Pro託管解決方案（英國）

只有當您選擇英國作為時，才可使用這些選項 [商戶國家](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| 啟用此解決方案 | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在付款資訊步驟中顯示「快速結帳」 | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款適用來源 | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用國家/地區付款自 | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用SSL驗證 | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow Pro

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| 儲存庫已啟用 | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 儲存庫標題 | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的信用卡型別 | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款適用來源 | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用國家/地區付款自 | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用SSL驗證 | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要CVV專案 | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒絕異動，如果： | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS街道不符合 | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS Zip不相符 | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 國際AVS指標不符合 | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 卡片安全性代碼不符 | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 廠商 | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用Proxy | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 合作夥伴 | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 廠商 | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用Proxy | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用此解決方案 | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款適用來源 | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用國家/地區付款自 | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用SSL驗證 | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV專案可編輯 | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要CVV專案 | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送電子郵件確認 | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow連結

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| 合作夥伴 | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 廠商 | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用薪資流程連結 | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用快速簽出 | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序PayPal信用 | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款適用來源 | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用國家/地區付款自 | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用SSL驗證 | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV專案可編輯 | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要CVV專案 | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送電子郵件確認 | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 零小計簽出路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| 已啟用 | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 貨到付款路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| 已啟用 | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 銀行轉帳付款路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| 已啟用 | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 支票或匯票路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| 已啟用 | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將支票支付給 | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 採購單路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| 已啟用 | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 國際路徑

>[!INFO]
>
>可用的路徑取決於您選擇的 [商家國家/地區](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| SFTP認證 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用此解決方案 | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡設定 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒絕異動，如果： | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將支票支付給 | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送支票至 | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_nz/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_nz/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_nz/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 新訂單狀態 | `payment_nz/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_nz/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_nz/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_nz/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_nz/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_nz/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_nz/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_nz/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_nz/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_nz/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_nz/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_nz/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 簽章欄位 | `payment_nz/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_nz/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_nz/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_nz/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_nz/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_nz/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_nz/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_nz/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_nz/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_nz/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_nz/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_nz/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_nz/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_nz/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_nz/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_nz/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_nz/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_nz/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_hk/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_hk/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_hk/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 新訂單狀態 | `payment_hk/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_hk/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_hk/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_hk/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_hk/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_hk/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_hk/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_hk/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_hk/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_hk/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_hk/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_hk/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_hk/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_hk/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_hk/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_hk/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_hk/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_hk/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_hk/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_hk/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_hk/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_hk/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_hk/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 沙箱模式 | `payment_hk/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_hk/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_hk/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_hk/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_hk/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_hk/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_hk/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將支票支付給 | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_es/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_es/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_es/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 設定檔ID | `payment_es/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |
| 新訂單狀態 | `payment_es/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_es/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_es/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_es/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_es/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_es/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_es/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_es/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_es/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_es/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 安裝ID | `payment_es/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 遠端管理安裝ID | `payment_es/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_es/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_es/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 簽章欄位 | `payment_es/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試模式 | `payment_es/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_es/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_es/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_es/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_es/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_es/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_es/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_es/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_es/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_es/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_es/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_es/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_es/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_es/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_es/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_es/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_es/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_it/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_it/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_it/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 新訂單狀態 | `payment_it/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_it/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_it/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_it/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_it/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_it/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_it/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_it/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_it/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_it/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_it/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_it/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 簽章欄位 | `payment_it/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_it/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_it/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_it/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_it/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_it/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_it/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_it/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_it/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_it/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_it/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_it/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_it/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_it/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_it/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_it/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_it/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_it/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_fr/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_fr/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_fr/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 新訂單狀態 | `payment_fr/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_fr/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_fr/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_fr/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_fr/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_fr/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_fr/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_fr/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_fr/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_fr/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_fr/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_fr/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_fr/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_fr/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_fr/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_fr/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_fr/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_fr/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_fr/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_fr/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_fr/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_fr/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_fr/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_fr/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_fr/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_fr/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_fr/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_fr/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_fr/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_jp/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_jp/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_jp/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_jp/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_jp/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_jp/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_jp/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_jp/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_jp/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_jp/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_jp/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_jp/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_jp/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_jp/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_jp/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_jp/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_jp/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_jp/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_jp/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_jp/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_jp/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_jp/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_jp/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_jp/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_jp/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_jp/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_jp/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_jp/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_jp/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_jp/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_jp/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡設定 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒絕異動，如果： | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將支票支付給 | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送支票至 | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_au/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_au/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_au/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 商家ID | `payment_au/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |
| 設定檔ID | `payment_au/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |
| 新訂單狀態 | `payment_au/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_au/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_au/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_au/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_au/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_au/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_au/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_au/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_au/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_au/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 安裝ID | `payment_au/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_au/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_au/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 簽章欄位 | `payment_au/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_au/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試模式 | `payment_au/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_au/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_au/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_au/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_au/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_au/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_au/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_au/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_au/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_au/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_au/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_au/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_au/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_au/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_au/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_au/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_au/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用此解決方案 | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡設定 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒絕異動，如果： | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡設定 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒絕異動，如果： | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_ca/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_ca/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_ca/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_ca/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_ca/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_ca/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_ca/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_ca/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_ca/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_ca/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_ca/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_ca/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_ca/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_ca/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 簽章欄位 | `payment_ca/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_ca/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_ca/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_ca/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_ca/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_ca/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_ca/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_ca/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_ca/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_ca/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_ca/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_ca/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_ca/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_ca/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_ca/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_ca/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_ca/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_ca/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送電子郵件給客戶 | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_other/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_other/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_other/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_other/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_other/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_other/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_other/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_other/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_other/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_other/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_other/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_other/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_other/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_other/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 簽章欄位 | `payment_other/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_other/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_other/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_other/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_other/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_other/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_other/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_other/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_other/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_other/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_other/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_other/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_other/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_other/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_other/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_other/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_other/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_other/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_de/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_de/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_de/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 新訂單狀態 | `payment_de/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_de/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_de/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_de/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_de/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_de/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_de/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_de/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_de/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_de/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_de/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_de/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 簽章欄位 | `payment_de/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試模式 | `payment_de/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_de/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_de/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_de/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_de/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_de/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_de/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_de/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_de/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_de/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_de/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_de/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_de/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_de/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_de/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_de/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_de/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將支票支付給 | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_gb/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_gb/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_gb/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 新訂單狀態 | `payment_gb/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_gb/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_gb/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_gb/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_gb/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_gb/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_gb/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_gb/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_gb/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_gb/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 交易的MD5密碼 | `payment_gb/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_gb/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_gb/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 簽章欄位 | `payment_gb/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_gb/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_gb/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_gb/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_gb/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_gb/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_gb/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_gb/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_gb/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_gb/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_gb/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_gb/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_gb/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_gb/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_gb/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_gb/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_gb/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_gb/eway/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排程擷取 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡設定 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒絕異動，如果： | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用PayPal點數 | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡設定 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒絕異動，如果： | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排程擷取 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家頁面樣式 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開立所有專案的商業發票 | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 指示 | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將支票支付給 | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款動作 | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 標題 | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訂單狀態 | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的貨幣 | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 偵錯 | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡型別 | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡驗證 | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自適用國家/地區的付款 | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 來自特定國家的付款 | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小訂購總計 | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大訂單總計 | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序順序 | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `payment_us/cybersource/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_us/cybersource/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_us/cybersource/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 新訂單狀態 | `payment_us/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_us/cybersource/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_us/cybersource/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_us/cybersource/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_us/cybersource/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最小訂購總計 | `payment_us/cybersource/min_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 最大訂單總計 | `payment_us/cybersource/max_order_total` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_us/cybersource/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_us/worldpay/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_us/worldpay/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 允許編輯聯絡資訊 | `payment_us/worldpay/fix_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 隱藏連絡資訊 | `payment_us/worldpay/hide_contact` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 簽章欄位 | `payment_us/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_us/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試的付款動作 | `payment_us/worldpay/test_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_us/worldpay/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_us/worldpay/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家/地區的付款 | `payment_us/worldpay/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將「訂單狀態」設定為CVV疑似詐騙 | `payment_us/worldpay/cvv_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 將郵遞區號AVS的訂單狀態設定為疑似詐騙 | `payment_us/worldpay/avs_fraud_case` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_us/worldpay/sort_order` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 已啟用 | `payment_us/eway/active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 連線型別 | `payment_us/eway/connection_type` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 標題 | `payment_us/eway/title` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 付款動作 | `payment_us/eway/payment_action` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 偵錯 | `payment_us/eway/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 信用卡型別 | `payment_us/eway/cctypes` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自適用國家/地區的付款 | `payment_us/eway/allowspecific` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 來自特定國家的付款 | `payment_us/eway/specificcountry` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 排序順序 | `payment_us/eway/sort_order` |  |

{style="table-layout:auto"}
