---
title: 一般設定路徑參考
description: 請參閱一般和進階設定值清單。
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---

# 一般和進階設定路徑參考

本主題列出一般和進階設定路徑，以及 _not_ [敏感值和系統特定值](config-reference-sens.md). 此 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將這些值寫入共用組態檔， `app/etc/config.php`，這應該是在原始檔控制中。

若要選擇性地覆寫任何組態設定或設定敏感設定，請參閱 [使用環境變數來覆寫組態設定](override-config-settings.md#environment-variables).

## 一般類別

本節列出變數名稱和設定路徑，以供管理員中的選項使用。 **商店** >設定> **設定** > **一般**.

### 一般路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** >一般> **一般**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 敏感？ |
|--------------|--------------|--------------|--------------|
| 預設國家 | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 允許國家/地區 | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 郵遞區號為選填，適用於 | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 歐盟國家 | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 熱門目的地 | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 以下專案需要狀態： | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 若國家/地區選擇州，則允許選擇州 | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 時區 | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 地區設定 | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 重量單位 | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 一週的第一天 | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 週末 | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 存取限制 | `general/restriction/is_active` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |
| 限制模式 | `general/restriction/mode` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |
| 啟動頁面 | `general/restriction/http_redirect` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |
| 登陸頁面 | `general/restriction/cms_page` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |
| HTTP回應 | `general/restriction/http_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |
| 存放區名稱 | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 商店電話號碼 | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 商店營業時間 | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 國家 | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 地區/州 | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 郵遞區號 | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 城市 | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 街道地址 | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 街道地址行2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| VAT編號 | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 啟用單一存放區模式 | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |

{style="table-layout:auto"}

### 網頁路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **一般** > **Web**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 將存放區代碼新增至Url | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動重新導向至基本URL | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用Web伺服器重寫 | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在店面上使用安全URL | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在管理員中使用安全URL | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用HTTP嚴格傳輸安全性(HSTS) | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 升級不安全的請求 | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Offloader標題 | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| cms首頁 | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS無路由頁面 | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS無Cookie頁面 | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示CMS頁面的階層連結 | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie期限 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 僅使用HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie限制模式 | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證REMOTE_ADDR | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證HTTP_VIA | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證HTTP_X_FORWARDED_FOR | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證HTTP_USER_AGENT | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在店面使用SID | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果停用Cookie，則重新導向至CMS頁面 | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果JavaScript已停用，則顯示通知 | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果本機儲存已停用，則顯示通知 | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 貨幣設定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **一般** > **貨幣設定**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 基本貨幣 | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 預設顯示貨幣 | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許的貨幣 | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo金融交易平台 | `TBD` |  |
| Fixer.io | `TBD` |  |
| Webservicex | `TBD` |  |
| 連線逾時（以秒為單位） | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 連線逾時（以秒為單位） | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 連線逾時（以秒為單位） | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已啟用 | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 服務 | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件收件者 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件寄件者 | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件範本 | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 連絡人路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **一般** > **連絡人**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 啟用與我們連絡 | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 傳送電子郵件至 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件寄件者 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子郵件範本 | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 報表路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **一般** > **報表**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 年初至今開始 | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 目前月份開始 | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 內容管理路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **一般** > **內容管理**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 啟用WYSIWYG編輯器 | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 對目錄的WYSIWYG中的媒體內容使用靜態URL | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用階層功能 | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用階層中繼資料 | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 階層功能表的預設配置 | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### New Relic報告路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **一般** > **New Relic報告**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 啟用New Relic整合 | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Relic應用程式名稱 | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用Cron | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 進階類別

本節列出「管理」下方的選項可用的變數名稱和設定路徑。 **商店** >設定> **設定** > **進階**.

### 管理員路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **進階** > **管理員**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 忘記密碼電子郵件範本 | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 忘記並重設電子郵件寄件者 | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用者通知範本 | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟動頁面 | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用自訂管理員URL | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用自訂管理路徑 | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理員帳戶共用 | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼重設保護型別 | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 復原連結有效期（小時） | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼重設請求的最大數量 | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼重設請求之間的最短時間 | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將秘密金鑰新增至URL | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 登入區分大小寫 | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理工作階段存留期（秒） | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 鎖定帳戶的最大登入失敗次數 | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 鎖定時間（分鐘） | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼存留期（天） | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密碼變更 | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用圖表 | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在管理員中啟用驗證碼 | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 字型 | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顯示模式 | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 嘗試登入失敗的次數 | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證碼逾時（分鐘） | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 符號數 | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 驗證碼中使用的符號 | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 區分大小寫 | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用的動作 | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 系統路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **進階** > **系統**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 成功的訊息存留期 | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重試以下時間後正在處理的訊息： | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗的訊息存留期 | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新訊息存留期 | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 產生排程間隔 | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 提前排程 | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果未於以下時間內執行，則會遺漏： | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 歷史記錄清理間隔 | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功歷程記錄期限 | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗歷程記錄期限 | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用個別程式 | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 產生排程間隔 | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 提前排程 | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 如果未於以下時間內執行，則會遺漏： | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 歷史記錄清理間隔 | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功歷程記錄期限 | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗歷程記錄期限 | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 產生排程間隔 | `system/cron/staging/schedule_generate_every` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 提前排程 | `system/cron/staging/schedule_ahead_for` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 如果未於以下時間內執行，則會遺漏： | `system/cron/staging/schedule_lifetime` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 歷史記錄清理間隔 | `system/cron/staging/history_cleanup_every` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 成功歷程記錄期限 | `system/cron/staging/history_success_lifetime` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 失敗歷程記錄期限 | `system/cron/staging/history_failure_lifetime` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 使用個別程式 | `system/cron/staging/use_separate_process` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 產生排程間隔 | `system/cron/catalog/event/schedule_generate_every` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 提前排程 | `system/cron/catalog/event/schedule_ahead_for` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 如果未於以下時間內執行，則會遺漏： | `system/cron/catalog/event/schedule_lifetime` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 歷史記錄清理間隔 | `system/cron/catalog/event/history_cleanup_every` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 成功歷程記錄期限 | `system/cron/catalog/event/history_success_lifetime` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 失敗歷程記錄期限 | `system/cron/catalog/event/history_failure_lifetime` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 使用個別程式 | `system/cron/catalog/event/use_separate_process` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 使用個別程式 | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 停用電子郵件通訊 | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 設定傳迴路徑 | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 回訪路徑電子郵件 | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已安裝貨幣 | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用HTTPS取得摘要 | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 更新頻率 | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 上次更新 | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用排定的備份 | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 備份型別 | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 維護模式 | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 記錄專案存留期，天 | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 記錄封存頻率 | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 快取應用程式 | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 公開內容的TTL | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 寬限期 | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 匯出設定 | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 記錄中儲存的天數 | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 媒體儲存 | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 選取媒體資料庫 | `system/media_storage_configuration/media_database` （Commerce 2.4.3已棄用） | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 環境更新時間 | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 儲存檔案，天 | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用排定的檔案記錄清理 | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻率 | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 錯誤電子郵件範本 | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 開發人員路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **進階** > **開發人員**.

| 名稱 | 設定路徑 | 僅限Commerce？ |
|--------------|--------------|--------------|
| 工作流程型別 | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允許符號連結 | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 縮制Html | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用店面的範本路徑提示 | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 為管理員啟用範本路徑提示 | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將區塊名稱新增至提示 | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 記錄至檔案 | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 記錄到syslog | `dev/syslog/syslog_logging` |  |
| 已針對店面啟用 | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 為管理員啟用 | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 合併JavaScript檔案 | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 啟用JavaScript套裝 | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小化JavaScript檔案 | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 翻譯策略 | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 將JS錯誤記錄到工作階段存放區 | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 合併CSS檔案 | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 縮制CSS檔案 | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 影像配接卡 | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 簽署靜態檔案 | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 非同步索引 | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 快取使用者定義的屬性 | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
