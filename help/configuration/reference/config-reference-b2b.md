---
title: B2B擴充功能設定路徑參考
description: 請參閱B2B相關設定值清單。
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# B2B擴充功能設定路徑參考

_這適用於已安裝Adobe Commerce適用的B2B執行個體。_

本主題列出Commerce Enterprise B2B擴充功能的設定路徑。 此 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將這些值寫入共用組態檔， `app/etc/config.php`，這應該是在原始檔控制中。

>[!INFO]
>
>此參考資料清單 _僅限_ Adobe Commerce的B2B專屬設定路徑。 此擴充功能包含Adobe Commerce的所有設定路徑。

如需這些設定路徑，請參閱：

- [付款設定路徑](config-reference-payment.md)
- [敏感和系統專屬設定路徑參考](config-reference-sens.md)

若要選擇性地覆寫任何組態設定或設定敏感設定，請參閱 [使用環境變數來覆寫組態設定](override-config-settings.md#environment-variables).

## 一般類別

本節列出變數名稱和設定路徑，以供管理員中的選項使用。 **[!UICONTROL Stores]** >設定> **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### B2B功能路徑

這些設定值可在的「管理員」中使用 **[!UICONTROL Stores]** >設定> **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| 名稱 | 設定路徑 | 已加密？ | 系統特定？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 啟用公司 | `btob/website_configuration/company_active` |  |  |  |
| 啟用共用目錄 | `btob/website_configuration/sharedcatalog_active` |  |  |  |
| 啟用B2B報價 | `btob/website_configuration/negotiablequote_active` |  |  |  |
| 啟用快速訂購 | `btob/website_configuration/quickorder_active` |  |  |  |
| 啟用請購單清單 | `btob/website_configuration/requisition_list_active` |  |  |  |
| 適用的付款方法 | `btob/default_b2b_payment_methods/applicable_payment_methods` |  |  |  |
| 付款方法 | `btob/default_b2b_payment_methods/available_payment_methods` |  |  |  |

{style="table-layout:auto"}

## 客戶類別

本節列出「管理」下方的選項可用的變數名稱和設定路徑。 **[!UICONTROL Stores]** >設定> **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### 公司設定路徑

這些設定值可在的「管理員」中使用 **[!UICONTROL Stores]** >設定> **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| 名稱 | 設定路徑 | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|
| 允許從店面註冊公司 | `company/general/allow_company_registration` |  |  |  |
| 公司註冊電子郵件收件者 | `company/email/company_registration` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將公司註冊電子郵件副本傳送至 | `company/email/company_registration_copy` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件複製方法 | `company/email/company_copy_method` |  |  |  |
| 預設公司註冊電子郵件 | `company/email/company_notify_admin_template` |  |  |  |
| 客戶相關電子郵件 | `company/email/heading_customer` |  |  |  |
| 預設銷售代表指派的電子郵件 | `company/email/customer_sales_representative_template` |  |  |  |
| 預設將公司指派給客戶電子郵件 | `company/email/customer_company_customer_assign_template` |  |  |  |
| 預設指派公司管理員電子郵件 | `company/email/customer_assign_super_user_template` |  |  |  |
| 預設公司管理員非使用中電子郵件 | `company/email/customer_inactivate_super_user_template` |  |  |  |
| 預設公司管理員已變更為成員電子郵件 | `company/email/customer_remove_super_user_template` |  |  |  |
| 預設客戶狀態作用中電子郵件 | `company/email/customer_account_activated_template` |  |  |  |
| 預設客戶狀態非使用中電子郵件 | `company/email/customer_account_locked_template` |  |  |  |
| 公司狀態變更 | `company/email/heading_company_status` |  |  |  |
| 公司狀態變更電子郵件收件者 | `company/email/company_status_change` |  |  |  |
| 將公司狀態變更電子郵件副本傳送至 | `company/email/company_status_change_copy` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件複製方法 | `company/email/company_status_copy_method` |  |  |  |
| 預設公司狀態變更為使用中1電子郵件 | `company/email/company_status_pending_approval_to_active_template` |  |  |  |
| 預設公司狀態變更為使用中2電子郵件 | `company/email/company_status_rejected_blocked_to_active_template` |  |  |  |
| 預設公司狀態變更為已拒絕的電子郵件 | `company/email/company_status_rejected_template` |  |  |  |
| 預設公司狀態變更為封鎖的電子郵件 | `company/email/company_status_blocked_template` |  |  |  |
| 預設公司狀態變更為未決核准電子郵件 | `company/email/company_status_pending_approval_template` |  |  |  |
| 公司評價 | `company/email/heading_company_credit` |  |  |  |
| 公司信用變更電子郵件寄件者 | `company/email/company_credit_change` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將公司信用變更電子郵件副本傳送至 | `company/email/company_credit_change_copy` |  |  |  |
| 傳送電子郵件複製方法 | `company/email/company_credit_copy_method` |  |  |  |
| 已分配的電子郵件範本 | `company/email/credit_allocated_email_template` |  |  |  |
| 已更新電子郵件範本 | `company/email/credit_updated_email_template` |  |  |  |
| 已償還電子郵件範本 | `company/email/credit_reimbursed_email_template` |  |  |  |
| 已退款的電子郵件範本 | `company/email/credit_refunded_email_template` |  |  |  |
| 回覆的電子郵件範本 | `company/email/credit_reverted_email_template` |  |  |  |

{style="table-layout:auto"}

### 請購單清單路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **客戶** > **請購單清單**.

| 名稱 | 設定路徑 | 已加密？ | 系統特定？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 請購單清單數量 | `requisitionlist/general/number_requisition_lists` |  |  |  |

{style="table-layout:auto"}

## 銷售類別

本節列出「管理」下方的選項可用的變數名稱和設定路徑。 **商店** >設定> **設定** > **銷售**.

### 銷售電子郵件路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **銷售電子郵件**.

| 名稱 | 設定路徑 | 已加密？ | 系統特定？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 已啟用 | `sales_email/quote/enabled` |  |  |  |
| 已更新報價範本（給採購員） | `sales_email/quote/updated_buyer_template` |  |  |  |
| 已拒絕報價範本（給採購員） | `sales_email/quote/declined_buyer_template` |  |  |  |
| 新報價範本（至賣方） | `sales_email/quote/new_seller_template` |  |  |  |
| 更新報價範本（至賣方） | `sales_email/quote/updated_seller_template` |  |  |  |
| 報價到期（48小時內） | `sales_email/quote/expire_two_days_template` |  |  |  |
| 報價到期（24小時內） | `sales_email/quote/expire_one_day_template` |  |  |  |
| 到期日重設 | `sales_email/quote/expire_reset_template` |  |  |  |
| 傳送報價電子郵件副本至 | `sales_email/quote/copy_to` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送報價電子郵件複製方法 | `sales_email/quote/copy_method` |  |  |  |

{style="table-layout:auto"}

### 引號路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **引號**.

| 名稱 | 設定路徑 | 已加密？ | 系統特定？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 最小金額 | `quote/general/minimum_amount` |  |  |  |
| 最小數量訊息 | `quote/general/minimum_amount_message` |  |  |  |
| 預設有效期 | `quote/general/default_expiration_period` |  |  |  |
| 上傳的檔案格式 | `quote/attached_files/file_formats` |  |  |  |
| 檔案大小上限 | `quote/attached_files/maximum_file_size` |  |  |  |
| 最小金額 | `quote/general/minimum_amount` |  |  |  |
| 最小數量訊息 | `quote/general/minimum_amount_message` |  |  |  |
| 預設有效期 | `quote/general/default_expiration_period` |  |  |  |
| 上傳的檔案格式 | `quote/attached_files/file_formats` |  |  |  |
| 檔案大小上限 | `quote/attached_files/maximum_file_size` |  |  |  |

{style="table-layout:auto"}

## 付款方式路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **付款方法**.

>[!INFO]
>
>可用的路徑取決於您選擇的商家國家/地區。

| 名稱 | 設定路徑 | 已加密？ | 系統特定？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 已啟用 | `payment/au/companycredit/active` |  |  |  |
| 標題 | `payment/au/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/au/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/au/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/au/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/au/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/au/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/au/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/es/companycredit/active` |  |  |  |
| 標題 | `payment/es/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/es/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/es/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/es/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/es/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/es/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/es/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/companycredit/active` |  |  |  |
| 標題 | `payment/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/nz/companycredit/active` |  |  |  |
| 標題 | `payment/nz/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/nz/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/nz/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/nz/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/nz/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/nz/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/nz/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/us/companycredit/active` |  |  |  |
| 標題 | `payment/us/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/us/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/us/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/us/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/us/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/us/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/us/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/gb/companycredit/active` |  |  |  |
| 標題 | `payment/gb/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/gb/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/gb/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/gb/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/gb/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/gb/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/gb/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/de/companycredit/active` |  |  |  |
| 標題 | `payment/de/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/de/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/de/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/de/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/de/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/de/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/de/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/other/companycredit/active` |  |  |  |
| 標題 | `payment/other/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/other/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/other/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/other/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/other/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/other/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/other/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/ca/companycredit/active` |  |  |  |
| 標題 | `payment/ca/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/ca/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/ca/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/ca/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/ca/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/ca/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/ca/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/hk/companycredit/active` |  |  |  |
| 標題 | `payment/hk/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/hk/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/hk/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/hk/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/hk/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/hk/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/hk/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/jp/companycredit/active` |  |  |  |
| 標題 | `payment/jp/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/jp/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/jp/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/jp/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/jp/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/jp/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/jp/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/fr/companycredit/active` |  |  |  |
| 標題 | `payment/fr/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/fr/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/fr/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/fr/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/fr/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/fr/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/fr/companycredit/sort_order` |  |  |  |
| 已啟用 | `payment/it/companycredit/active` |  |  |  |
| 標題 | `payment/it/companycredit/title` |  |  |  |
| 新訂單狀態 | `payment/it/companycredit/order_status` |  |  |  |
| 來自適用國家/地區的付款 | `payment/it/companycredit/allowspecific` |  |  |  |
| 來自特定國家的付款 | `payment/it/companycredit/specificcountry` |  |  |  |
| 最小訂購總計 | `payment/it/companycredit/min_order_total` |  |  |  |
| 最大訂單總計 | `payment/it/companycredit/max_order_total` |  |  |  |
| 排序順序 | `payment/it/companycredit/sort_order` |  |  |  |

{style="table-layout:auto"}
