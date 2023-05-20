---
title: 客戶個人資訊參考（1.x版）
description: 瞭解Magento1.x中客戶個人資訊的資料流和資料庫實體對應。
exl-id: 8b01418d-8ca1-48fc-9577-a324ed3109d1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 0%

---

# 客戶個人資訊參考（1.x版）

>[!NOTE]
>
>這是一系列主題中的一個，可協助Adobe Commerce和Magento Open Source商家及開發人員為遵守隱私權法規做好準備。 請洽詢您的法律顧問，判斷您的企業是否及如何遵守任何法律義務。

開發隱私權法規的規範遵循程式時，請參考下列資料流圖表和資料庫實體對應，例如：

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## 資料流圖表

資料流圖表顯示客戶和管理員可以在店面和管理員上輸入和擷取的資料型別。

### 前端資料輸入點

註冊帳戶時、結帳期間和類似事件時，使用者可以輸入客戶、地址和付款資訊。

![前端資料輸入點](../../assets/security-compliance/frontend-data-entry-points.svg)

### 前端資料存取點

客戶登入並檢視數個不同頁面或簽出時，Commerce會載入客戶資訊。

![前端資料存取點](../../assets/security-compliance/frontend-data-access-points.svg)

### 後端資料輸入點

商家可以輸入來自管理員的客戶、地址及付款資訊，以建立客戶或訂單。

![後端資料輸入點](../../assets/security-compliance/backend-data-entry-points.svg)

### 後端資料存取點

當商家檢視幾種型別的網格、按一下網格以檢視詳細資訊時，Commerce會載入客戶資訊，並執行各種其他工作。

![後端資料存取點](../../assets/security-compliance/backend-data-access-points.svg)

## 資料庫實體

Magento1會將客戶資訊儲存在客戶、銷售和其他資料庫表格中。

### 客戶資料

Magento1會將客戶資訊儲存在 `customer_entity` 和 `customer_address_entity` 表格。 這兩個表格都有數個參考表格，可包含自訂客戶屬性。

#### `customer_entity` 和參考表格

下列欄位位於 `customer_entity`表格包含客戶資訊：

| 欄 | 資料型別 |
| --- | --- |
| `email` | varchar(255) |

這些表格參考 `customer_entity` 並且可以包含自訂客戶屬性：

| 表格 | 欄 | 資料型別 |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | 日期時間 |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | 文字 |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity` 和參考表格

下清單格參考 `customer_address_entity` 並且可以包含自訂客戶屬性：

| 表格 | 欄 | 資料型別 |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | 日期時間 |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | 文字 |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 訂單資料

此 `sales_flat_order` 和相關表格包含客戶名稱、帳單和送貨地址及相關資訊。

#### `sales_flat_order` 表格

下列欄位位於 `sales_order` 表格包含客戶資訊：

| 欄 | 資料型別 |
| --- | --- |
| `customer_id` | int(10) |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `remote_ip` | varchar(32) |

#### `sales_flat_order_address` 表格

此 `sales_flat_order_address` 表格包含客戶的地址。

| 欄 | 資料型別 |
| --- | --- |
| `customer_id` | int(10) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `firstname` | varchar(255) |
| `prefix` | varchar(255) |
| `suffix` | varchar(255) |
| `middlename` | varchar(255) |
| `company` | varchar(255) |
| `vat_id` | 文字 |

#### `sales_flat_order_grid` 表格

下列欄位位於 `sales_flat_order_grid` 表格包含客戶資訊：

| 欄 | 資料型別 |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### `sales_flat_order_payment` 表格

下列欄位位於 `sales_flat_order_payment` 表格包含客戶資訊：

| 欄 | 資料型別 |
| --- | --- |
| `cc_exp_month` | varchar(255) |
| `cc_ss_start_year` | varchar(255) |
| `echeck_bank_name` | varchar(128) |
| `echeck_type` | varchar(255) |
| `cc_ss_start_month` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_year` | varchar(255) |
| `echeck_routing_number` | varchar(255) |
| `echeck_account_name` | varchar(255) |

### 報價資料

引號包含客戶名稱、電子郵件、地址及相關資訊。

#### `sales_flat_quote` 表格

下列欄位位於 `sales_flat_quote` 表格包含客戶資訊：

| 欄 | 資料型別 |
| --- | --- |
| `customer_id` | int(10) |
| `customer_tax_class_id` | int(10) |
| `customer_group_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_suffix` | varchar(40) |
| `customer_dob` | 日期時間 |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `sales_flat_quote_address` 表格

下列欄位位於 `sales_flat_quote_address` 表格包含客戶資訊：

| 欄 | 資料型別 |
| --- | --- |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `fax` | varchar(255) |

#### `sales_flat_quote_payment` 表格

此 `sales_flat_quote_payment` 表格包含信用卡資訊和其他交易資訊。

| 欄 | 資料型別 |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | smallint(5) |
| `cc_exp_year` | smallint(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | smallint(5) |
| `cc_ss_start_year` | smallint(5) |

### 封存資料

下清單格和欄位包含客戶資訊：

| 表格 | 欄 | 資料型別 |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `customer_id` | int(10) |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar(255) |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar(255) |

### 銷售資料

下清單格和欄位包含客戶資訊：

| 表格 | 欄 | 資料型別 |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### RMA資料

下列RMA表格與欄位包含客戶資訊：

| 表格 | 欄 | 資料型別 |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar(255) |
| `enterprise_rma_grid` | `customer_id` | int(10) |
| `enterprise_rma_grid` | `customer_name` | varchar(255) |

### 其他資料

下清單格和欄位包含客戶資訊：

| 表格 | 欄 | 資料型別 |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar(128) |
| `core_email_queue_recipients` | `recipient_name` | varchar(255) |
| `customer_flowpassword` | `email` | varchar(255) |
| `customer_flowpassword` | `ip` | varchar(50) |
| `enterprise_giftregistry_person` | `email` | varchar(150) |
| `enterprise_giftregistry_person` | `firstname` | varchar(100) |
| `enterprise_giftregistry_person` | `lastname` | varchar(100) |
| `enterprise_giftregistry_person` | `middlename` | 文字 |
| `enterprise_invitation` | `customer_id` | int(10) |
| `enterprise_invitation` | `email` | varchar(255) |
| `enterprise_invitation` | `referral_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `customer_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `emails_failed` | smallint(5) |
| `enterprise_scheduled_operations` | `email_receiver` | varchar(150) |
| `enterprise_scheduled_operations` | `email_sender` | varchar(150) |
| `gift_message` | `customer_id` | int(10) |
| `gift_message` | `recipient` | varchar(255) |
| `gift_message` | `sender` | varchar(255) |
| `newsletter_subscriber` | `customer_id` | int(10) |
| `newsletter_subscriber` | `subscriber_email` | varchar(150) |
| `persistent_session` | `customer_id` | int(10) |
| `persistent_session` | `info` | 文字 |
| `poll_vote` | `customer_id` | int(10) |
| `poll_vote` | `ip_address` | varbinary(16) |
| `rating_option_vote` | `customer_id` | int(10) |
| `rating_option_vote` | `remote_ip` | varchar(50) |
| `rating_option_vote` | `remote_ip_long` | varbinary(516) |
| `send_friend_log` | `ip` | varbinary(16) |

參考客戶的其他表格：

- `catalog_compare_item`
- `downloadable_link_purchased`
- `enterprise_customerbalance`
- `enterprise_customersegment_customer`
- `enterprise_giftregistry_entity`
- `enterprise_reminder_rule_log`
- `enterprise_reward`
- `log_customer`
- `log_visitor_online`
- `oauth_token`
- `product_alert_price`
- `product_alert_stock`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `sales_billing_agreement`
- `sales_flat_shipment`
- `sales_recurring_profile`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `tag`
- `tag_relation`
- `wishlist`
