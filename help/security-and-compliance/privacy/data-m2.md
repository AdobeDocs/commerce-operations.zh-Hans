---
title: 客戶個人資訊參考（2.x版）
description: 瞭解Adobe Commerce和Magento Open Source2.x中客戶個人資訊的資料流圖表和資料庫實體對應。
exl-id: f08f4f93-a7b6-4c43-bc07-f159822dc528
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# 客戶個人資訊參考（2.x版）

>[!NOTE]
>
>這是一系列主題中的一個，可協助Adobe Commerce和Magento Open Source商家及開發人員為遵守隱私權法規做好準備。 請洽詢您的法律顧問，判斷您的企業是否及如何遵守任何法律義務。

開發隱私權法規的規範遵循程式時，請參考下列資料流圖表和資料庫實體對應，例如：

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## 資料流圖表

資料流圖表顯示客戶和管理員可以輸入並從店面和管理員中擷取的資料型別。

### 前端資料輸入點

註冊帳戶時、結帳期間和類似事件時，使用者可以輸入客戶、地址和付款資訊。

![前端資料輸入點](../../assets/security-compliance/frontend-data-entry-points.svg)

### 前端資料存取點

客戶登入並檢視數個不同頁面或簽出時，Adobe Commerce和Magento Open Source會載入客戶資訊。

![前端資料存取點](../../assets/security-compliance/frontend-data-access-points.svg)

### 後端資料輸入點

商家從管理員建立客戶或訂單時，可以輸入客戶資訊、地址資料及付款資料。

![後端資料輸入點](../../assets/security-compliance/backend-data-entry-points.svg)

### 後端資料存取點

當商家檢視幾種型別的網格、按一下網格以檢視詳細資訊並執行各種其他工作時，Adobe Commerce和Magento Open Source會載入客戶資訊。

![後端資料存取點](../../assets/security-compliance/backend-data-access-points.svg)

## 資料庫實體

Adobe Commerce和Magento Open Source主要將客戶特定的資訊儲存在客戶、地址、訂單、報價和付款表中。 其他表格則包含對客戶ID的參照。

### 客戶資料

Adobe Commerce和Magento Open Source可設定為儲存下列客戶屬性：

- 出生日期
- 電子郵件
- 名字
- 性別
- 姓氏
- 中間名/首字母
- 名稱首碼
- 名稱字尾

>[!NOTE]
>
>為了遵循目前的安全性和隱私權最佳實務，在收集或處理這類資料之前，請務必瞭解客戶完整出生日期（月、日、年）及其他個人識別碼（例如全名）的儲存可能會帶來的任何法律和安全風險。

#### `customer_entity` 和&#39;customer_entity&#39;參考

下列欄位位於 `customer_entity` 表格包含客戶資訊：

| 欄 | 資料型別 |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | 日期 |
| `gender` | smallint(5) |

這些表格參考 `customer_entity` 並且可以包含自訂客戶屬性：

| 表格 | 欄 | 資料型別 |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | 日期時間 |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | 文字 |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` 表格

下列欄位位於 `customer_grid_flat` 表格包含客戶資訊：

| 欄 | 資料型別 |
| -------------------- | ------------ |
| `name` | 文字 |
| `email` | varchar(255) |
| `dob` | 日期 |
| `gender` | int(11) |
| `shipping_full` | 文字 |
| `billing_full` | 文字 |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | varchar(255) |

### 位址資料

Adobe Commerce和Magento Open Source會儲存下列客戶屬性：

- 城市
- 公司
- 國家
- 傳真
- 名字
- 姓氏
- 中間名/首字母
- 名稱首碼
- 名稱字尾
- 電話號碼
- 州/省
- 州/省ID
- 街道地址
- VAT編號
- 郵遞區號

#### `customer_address_entity` 和 `customer_address_entity` 引用

下列欄位位於 `customer_address_entity` 表格包含客戶資訊：

| 欄 | 資料型別 |
| ------------ | ------------ |
| `city` | varchar(255) |
| `company` | varchar(255) |
| `country_id` | varchar(255) |
| `fax` | varchar(255) |
| `firstname` | varchar(255) |
| `lastname` | varchar(255) |
| `middlename` | varchar(255) |
| `postcode` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `street` | 文字 |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

這些表格參考 `customer_address_entity` 並且可以包含自訂客戶屬性：

| 表格 | 欄 | 資料型別 |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | 日期時間 |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | 文字 |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 訂單資料

此 `sales_order` 和相關表格包含客戶名稱、帳單和送貨地址及相關資料。

#### `sales_order` 表格

下列欄位位於 `sales_order` 表格包含客戶資訊：

| 欄 | 資料型別 |
| --------------------- | ------------ |
| `customer_dob` | 日期時間 |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_group_id` | int(11) |
| `customer_id` | int(10) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `quote_address_id` | int(11) |
| `remote_ip` | varchar(32) |
| `x_forwarded_for` | varchar(32) |

#### `sales_order_address` 表格

此 `sales_order_address` 表格包含客戶的地址。

| 欄 | 資料型別 |
| --------------------- | ------------ |
| `customer_address_id` | int(11) |
| `quote_address_id` | int(11) |
| `region_id` | int(11) |
| `customer_id` | int(11) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | varchar(255) |
| `suffix` | varchar(255) |
| `company` | varchar(255) |

#### `sales_order_grid` 表格

下列欄位位於 `sales_order_grid` 表格包含客戶資訊：

| 欄 | 資料型別 |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### 報價資料

引號包含客戶名稱、電子郵件、地址及相關資訊。

#### `quote` 表格

下列欄位位於 `quote` 表格包含客戶資訊：

| 欄 | 資料型別 |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | 日期時間 |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address` 表格

下列欄位位於 `quote_address` 表格包含客戶資訊：

| 欄 | 資料型別 |
| ------------- | ------------ |
| `customer_id` | int(10) |
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
| `region_id` | int(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | varchar(255) |
| `fax` | varchar(255) |

### 付款資料

此 `sales_order_payment` 表格包含信用卡資訊和其他交易資訊。

| 欄 | 資料型別 |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | varchar(128) |
| `additional_information` | 文字 |

### 邀請資料

可以設定Adobe Commerce和Magento Open Source，讓客戶可以傳送邀請函給私人銷售和活動。

#### `magento_invitation` 表格

此 `magento_invitation` 表格包含客戶ID、電子郵件和轉介ID。

| 欄 | 資料型別 |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` 表格

此 `magento_invitation_track` 表格也包含客戶資訊。

| 欄 | 資料型別 |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### 參考客戶的雜項表格

下清單格包含 `customer_id` 欄：

- `catalog_compare_item`
- `catalog_product_frontend_action`
- `downloadable_link_purchased`
- `magento_customerbalance`
- `magento_customersegment_customer`
- `magento_reward`
- `magento_rma`
- `oauth_token`
- `paypal_billing_agreement`
- `persistent_session`
- `product_alert_price`
- `product_stock_alert`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `wishlist`
