---
title: 敏感路徑和系統特定路徑
description: 請參閱系統專屬和敏感設定值清單。
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '3702'
ht-degree: 0%

---

# 敏感和系統專屬設定

本主題列出系統特定和敏感設定的組態路徑：

- 此 [`magento app:config:dump` 命令](../cli/export-configuration.md) 將系統特定設定寫入系統特定組態檔， `app/etc/env.php`，應 _not_ 在原始檔控制中。 它也會將所有Commerce執行個體的共用設定寫入 `app/etc/config.php`，此檔案 _應該_ 在原始檔控制中。
- 此 [`magento config:sensitive:set` 命令](../cli/set-configuration-values.md) 將敏感設定寫入 `app/etc/env.php`.

   您也可以使用設定變數設定敏感值，如中所述 [使用環境變數來覆寫組態設定](../reference/override-config-settings.md#environment-variables).

如需其他設定路徑的清單，請參閱：

- [除付款以外的所有設定路徑](../reference/config-reference-general.md)
- [付款設定路徑](../reference/config-reference-payment.md).

>[!INFO]
>
>本主題中列出的所有設定路徑都區分大小寫。 此 `System-specific?` 欄會顯示哪些值也是系統專屬的值。

## 一般類別敏感和系統特定路徑

本節列出變數名稱和設定路徑，以供管理員中的選項使用。 **商店** >設定> **設定** > **一般**.

### 網路路徑敏感路徑和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **一般** > **Web**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 基本URL | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 基本連結URL | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 靜態檢視檔案的基本URL | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 使用者媒體檔案的基本URL | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 安全基底URL | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 安全基本連結URL | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 靜態檢視檔案的安全基底URL | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 使用者媒體檔案的安全基底URL | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 預設網頁URL | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 預設無路由URL | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| Cookie路徑 | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| Cookie網域 | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| Cookie期限 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 僅使用HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| Cookie限制模式 | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 貨幣設定敏感和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **一般** > **貨幣設定**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件者 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 儲存區分電子郵件地址和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **電子郵件設定** > **一般** > **存放區電子郵件地址**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 寄件者名稱 | `trans_email/ident_general/name` |  |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者電子郵件 | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者名稱 | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者電子郵件 | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者名稱 | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者電子郵件 | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者名稱 | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者電子郵件 | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者名稱 | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 寄件者電子郵件 | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 聯絡敏感和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **一般** > **連絡人**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 傳送電子郵件至 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件寄件者 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電子郵件範本 | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### New Relic報表敏感路徑和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **一般** > **New Relic報告**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic帳戶ID | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| New Relic應用程式識別碼 | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| New Relic API金鑰 | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Insights API金鑰 | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| NEW RELIC API URL | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Insights API URL | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 客戶類別敏感和系統特定路徑

本節列出「管理」下方的選項可用的變數名稱和設定路徑。 **商店** >設定> **設定** > **客戶**.

### 客戶設定敏感和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **客戶** > **客戶設定**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 預設電子郵件網域 | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## 目錄類別

本節列出「管理」下方的選項可用的變數名稱和設定路徑。 **商店** >設定> **設定** > **目錄**.

### 目錄敏感路徑和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **目錄** > **目錄**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件者 | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| YouTube API金鑰 | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器主機名稱 | `catalog/search/solr_server_hostname` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器連線埠 | `catalog/search/solr_server_port` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器使用者名稱 | `catalog/search/solr_server_username` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器密碼 | `catalog/search/solr_server_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr伺服器路徑 | `catalog/search/solr_server_path` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch伺服器主機名稱 | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch伺服器連線埠 | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch索引首碼 | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 啟用ElasticsearchHTTP驗證 | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP使用者名稱 | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP密碼 | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| Elasticsearch伺服器逾時 | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP使用者名稱 | `catalog/search/elasticsearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| ElasticsearchHTTP密碼 | `catalog/search/elasticsearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Elasticsearch伺服器逾時 | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch伺服器主機名稱 | `catalog/search/opensearch_server_hostname` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| OpenSearch伺服器連線埠 | `catalog/search/opensearch_server_port` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| OpenSearch索引首碼 | `catalog/search/opensearch_index_prefix` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 啟用OpenSearch HTTP驗證 | `catalog/search/opensearch_enable_auth` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch HTTP使用者名稱 | `catalog/search/opensearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch HTTP密碼 | `catalog/search/opensearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| OpenSearch伺服器逾時 | `catalog/search/opensearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |

{style="table-layout:auto"}

>[!NOTE]
>
>Adobe Commerce 2.4.6中引入OpenSearch設定。

### 清查敏感路徑和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **目錄** > **詳細目錄**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Google API金鑰 | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### XML Sitemap敏感路徑和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **目錄** > **XML網站地圖**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件者 | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 銷售類別

本節列出「管理」下方的選項可用的變數名稱和設定路徑。 **商店** >設定> **設定** > **銷售**.

### 運送設定敏感和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **送貨設定**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 國家 | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 地區/州 | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 郵遞區號 | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 城市 | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址行2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時帳戶 | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 銷售電子郵件敏感和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **銷售電子郵件**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將訂單電子郵件副本傳送至 | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將訂單評論電子郵件副本傳送至 | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將發票電子郵件副本傳送至 | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將商業發票附註電子郵件副本傳送至 | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送出貨電子郵件副本至 | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將出貨評論電子郵件副本傳送至 | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將銷退折讓單電子郵件副本傳送至 | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將銷退折讓單備註電子郵件副本傳送至 | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將取車準備就緒電子郵件副本傳送至 | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 簽出敏感路徑和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **簽出**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將付款失敗的電子郵件副本傳送到 | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API敏感路徑和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **GOOGLE API**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 容器ID | `google/analytics/container_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 傳遞方法敏感和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **傳遞方法**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 閘道URL | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安全閘道URL | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 標題 | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用者ID | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 使用者ID | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取授權號碼 | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 追蹤XML URL | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 閘道XML URL | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 託運人編號 | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 偵錯 | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 帳戶ID | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 金鑰 | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 計量器編號 | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取識別碼 | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 偵錯 | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 帳號 | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 閘道URL | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱模式 | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 銷售敏感度與系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **銷售**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 連絡人姓名 | `sales/magento_rma/store_name` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `sales/magento_rma/address` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 城市 | `sales/magento_rma/city` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 州/省 | `sales/magento_rma/region_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 郵遞區號 | `sales/magento_rma/zip` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 國家 | `sales/magento_rma/country_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送RMA電子郵件副本至 | `sales_email/magento_rma/copy_to` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送RMA授權電子郵件副本至 | `sales_email/magento_rma_auth/copy_to` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送RMA備註電子郵件副本至 | `sales_email/magento_rma_comment/copy_to` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送RMA備註電子郵件副本至 | `sales_email/magento_rma_customer_comment/copy_to` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **銷售** > **GOOGLE API**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 帳號 | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 進階類別

本節列出「管理」下方的選項可用的變數名稱和設定路徑。 **商店** >設定> **設定** > **進階**.

### 管理員敏感和系統專屬路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **進階** > **管理員**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 自訂管理員URL | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自訂管理路徑 | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 系統敏感路徑和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **進階** > **系統**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 錯誤電子郵件收件者 | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取清單 | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 錯誤電子郵件寄件者 | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 開發人員敏感和系統特定路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **進階** > **開發人員**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 允許的IP （以逗號分隔） | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 進階類別

本節列出「管理」下方的選項可用的變數名稱和設定路徑。 **商店** >設定> **設定** > **進階**.

### 系統路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **進階** > **系統**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 主機 | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 連線埠(25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 後端主機 | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 後端連線埠 | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 開發人員路徑

這些設定值可在的「管理員」中使用 **商店** >設定> **設定** > **進階** > **開發人員**.

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 將JS錯誤記錄到工作階段儲存金鑰 | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## 付款敏感路徑和系統特定路徑

本節列出「管理」下方的選項可用的變數名稱和設定路徑。 **商店** >設定> **設定** > **銷售** > **付款**.

### 一般變數

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ |
|--------------|--------------|--------------|--------------|
| 商戶國家 | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

>[!INFO]
>
>您對此變數的選擇會決定 [國際路徑](#international-paths) 您可以使用。

### PayPal敏感路徑和系統特定路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 與PayPal商家帳戶相關聯的電子郵件（選用） | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家帳戶ID | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 發行者ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 登入 | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自訂端點主機名稱或IP位址 | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱模式 | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 偵錯模式 | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 偵錯模式 | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| SFTP認證 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Pro敏感路徑和系統特定路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 使用者 | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自訂路徑 | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 使用者 | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 合作夥伴 | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Proxy主機 | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Proxy連線埠 | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 偵錯模式 | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| SFTP認證 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 信用卡設定 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow連結敏感路徑和系統特定路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 使用者 | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密碼 | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 使用Proxy | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| Proxy主機 | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| Proxy連線埠 | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 偵錯模式 | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 用於取消URL和傳回URL的URL方法 | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 偵錯模式 | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| SFTP認證 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro敏感路徑和系統特定路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API使用者名稱 | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API密碼 | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API簽章 | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API憑證 | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Proxy主機 | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Proxy連線埠 | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱模式 | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| SFTP認證 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro託管敏感和系統特定路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 偵錯模式 | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| SFTP認證 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Braintree敏感和系統特定路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 商家ID | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 公開金鑰 | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 私密金鑰 | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家帳戶ID | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 帳戶商家ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 覆寫商家名稱 | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 電話 | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 支票/匯票路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 傳送支票至 | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送支票至 | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 國際路徑

| 名稱 | 設定路徑 | 僅限Commerce？ | 已加密？ | 系統特定？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 交易金鑰 | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_au/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_au/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_au/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_au/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 付款回應密碼 | `payment_au/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_au/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱模式 | `payment_au/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_au/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_au/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_au/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_au/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_au/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_au/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_es/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_es/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_es/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_es/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 付款回應密碼 | `payment_es/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_es/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_es/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 偵錯 | `payment_es/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_es/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_es/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_es/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_es/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_es/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_es/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_es/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_nz/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_nz/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_nz/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_nz/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_nz/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_nz/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_nz/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_nz/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_nz/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| Proxy主機 | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Proxy連線埠 | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 偵錯模式 | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 用於取消URL和傳回URL的URL方法 | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_us/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_us/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_us/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_us/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_us/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_us/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_us/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_us/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_us/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_us/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_us/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_gb/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_gb/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_gb/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_gb/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_gb/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_gb/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_gb/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_gb/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_gb/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_de/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_de/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_de/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_de/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 交易金鑰 | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款回應密碼 | `payment_de/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_de/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 偵錯 | `payment_de/worldpay/debug` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_de/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_de/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_de/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_de/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_de/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_de/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_de/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 閘道URL | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 交易金鑰 | `payment_other/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_other/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_other/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_other/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_other/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 付款回應密碼 | `payment_other/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_other/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_other/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_other/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_other/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_other/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_other/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_other/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_other/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_other/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_ca/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_ca/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_ca/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_ca/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 測試模式 | `payment_ca/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 付款回應密碼 | `payment_ca/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 遠端管理員授權密碼 | `payment_ca/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_ca/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_ca/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_ca/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_ca/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_ca/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_ca/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_ca/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_ca/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_hk/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_hk/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_hk/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_hk/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款回應密碼 | `payment_hk/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_hk/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_hk/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API金鑰 | `payment_hk/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_hk/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_hk/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_hk/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_hk/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_hk/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_jp/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_jp/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_jp/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_jp/cybersource/order_status` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 測試模式 | `payment_jp/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 付款回應密碼 | `payment_jp/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_jp/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_jp/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_jp/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_jp/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_jp/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_jp/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_jp/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_jp/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_jp/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_fr/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_fr/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_fr/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_fr/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 付款回應密碼 | `payment_fr/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_fr/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_fr/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_fr/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_fr/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_fr/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_fr/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_fr/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_fr/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_fr/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 閘道URL | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易詳細資料URL | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_it/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_it/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_it/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_it/cybersource/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 付款回應密碼 | `payment_it/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_it/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 測試模式 | `payment_it/worldpay/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 沙箱模式 | `payment_it/eway/sandbox_flag` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) |
| 即時API金鑰 | `payment_it/eway/live_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時API密碼 | `payment_it/eway/live_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 即時使用者端加密金鑰 | `payment_it/eway/live_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API金鑰 | `payment_it/eway/sandbox_api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱API密碼 | `payment_it/eway/sandbox_api_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙箱使用者端加密金鑰 | `payment_it/eway/sandbox_encryption_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API金鑰 | `fraud_protection/signifyd/api_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API URL | `fraud_protection/signifyd/api_url` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  | ![系統專用](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理安裝ID | `payment_au/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_au/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送支票至 | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_es/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_es/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理安裝ID | `payment_es/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 |
| SFTP認證 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_nz/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_nz/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_nz/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_nz/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_nz/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_nz/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款回應密碼 | `payment_nz/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理安裝ID | `payment_nz/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_nz/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_nz/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_us/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_us/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_us/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_us/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款回應密碼 | `payment_us/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理安裝ID | `payment_us/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_us/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_us/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送支票至 | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_gb/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_gb/cybersource/transaction_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_gb/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 存取金鑰 | `payment_gb/cybersource/access_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 秘密金鑰 | `payment_gb/cybersource/secret_key` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易金鑰 | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_gb/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款回應密碼 | `payment_gb/worldpay/response_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理安裝ID | `payment_gb/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理員授權密碼 | `payment_gb/worldpay/auth_password` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票支付給 | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送支票至 | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_de/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_de/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_de/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 遠端管理安裝ID | `payment_de/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_de/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票支付給 | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送支票至 | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_other/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_other/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_other/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理安裝ID | `payment_other/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_other/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票支付給 | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送支票至 | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新訂單狀態 | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_ca/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_ca/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_ca/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理安裝ID | `payment_ca/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_ca/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票支付給 | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送支票至 | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_hk/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_hk/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_hk/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理安裝ID | `payment_hk/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_hk/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 簽章欄位 | `payment_hk/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票支付給 | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送支票至 | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_jp/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_jp/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_jp/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |
| 遠端管理安裝ID | `payment_jp/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_jp/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 簽章欄位 | `payment_jp/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票支付給 | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送支票至 | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_fr/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_fr/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_fr/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理安裝ID | `payment_fr/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_fr/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 簽章欄位 | `payment_fr/worldpay/signature_fields` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP認證 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 將支票支付給 | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送支票至 | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登入ID | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 傳送電子郵件給客戶 | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家電子郵件 | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家ID | `payment_it/cybersource/merchant_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 設定檔ID | `payment_it/cybersource/profile_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安裝ID | `payment_it/worldpay/installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 遠端管理安裝ID | `payment_it/worldpay/admin_installation_id` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密碼 | `payment_it/worldpay/md5_secret` | ![Commerce-only](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}
