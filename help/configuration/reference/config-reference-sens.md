---
title: 敏感路径和系统特定路径
description: 了解Adobe Commerce的敏感和特定于系统的配置路径。 发现安全配置和环境变量管理。
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '4206'
ht-degree: 0%

---

# 敏感和特定于系统的设置

本主题列出了系统特定和敏感设置的配置路径：

- [`magento app:config:dump`命令](../cli/export-configuration.md)将特定于系统的设置写入特定于系统的配置文件`app/etc/env.php`，该文件应该&#x200B;_不_&#x200B;位于源代码控制中。 它还将所有Commerce实例的共享配置写入`app/etc/config.php`，此文件&#x200B;_应_&#x200B;在源代码管理中。
- [`magento config:sensitive:set`命令](../cli/set-configuration-values.md)将敏感设置写入`app/etc/env.php`。

  您还可以使用[使用环境变量覆盖配置设置](../reference/override-config-settings.md#environment-variables)中所述的配置变量来设置敏感值。

有关其他配置路径的列表，请参阅：

- [除支付以外的所有配置路径](../reference/config-reference-general.md)
- [付款配置路径](../reference/config-reference-payment.md)。

>[!INFO]
>
>本主题中列出的所有配置路径都是敏感的。 `System-specific?`列显示哪些值也特定于系统。

## 一般类别敏感路径和系统特定路径

此部分列出了&#x200B;**存储** >设置> **配置** > **常规**&#x200B;下的管理员中选项可用的变量名称和配置路径。

### Web路径敏感路径和系统特定路径

这些配置值在&#x200B;**存储** >设置> **配置** > **常规** > **Web**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 基本URL | `web/unsecure/base_url` |  | | 系统特定 | |
| 基本链接URL | `web/unsecure/base_link_url` |  | | 系统特定 | |
| 静态视图文件的基本URL | `web/unsecure/base_static_url` |  | | 系统特定 | |
| 用户媒体文件的基本URL | `web/unsecure/base_media_url` |  | | 系统特定 | |
| 安全基础URL | `web/secure/base_url` |  | | 系统特定 | |
| 安全基本链接URL | `web/secure/base_link_url` |  | | 系统特定 | |
| 静态视图文件的安全基本URL | `web/secure/base_static_url` |  | | 系统特定 | |
| 用户媒体文件的安全基本URL | `web/secure/base_media_url` |  | | 系统特定 | |
| 默认Web URL | `web/default/front` |  | | 系统特定 | |
| 默认无路由URL | `web/default/no_route` |  | | 系统特定 | |
| Cookie路径 | `web/cookie/cookie_path` |  | | 系统特定 | |
| Cookie域 | `web/cookie/cookie_domain` |  | | 系统特定 | |
| Cookie生命周期 | `web/cookie/cookie_lifetime` |  | | 系统特定 | |
| 仅使用HTTP | `web/cookie/cookie_httponly` |  | | 系统特定 | |
| Cookie限制模式 | `web/cookie/cookie_restriction` |  | | 系统特定 | |

{style="table-layout:auto"}

### 货币设置敏感且特定于系统的路径

这些配置值在&#x200B;**存储** >设置> **配置** > **常规** > **货币设置**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
| --- | --- | --- | --- | --- | --- |
| 错误电子邮件收件人 | `currency/import/error_email` |  | | | 敏感 |

{style="table-layout:auto"}

### 存储区分电子邮件地址和特定于系统的路径

这些配置值在&#x200B;**商店** >设置> **电子邮件配置** > **常规** > **商店电子邮件地址**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 发件人姓名 | `trans_email/ident_general/name` | | | | 敏感 |
| 发件人电子邮件 | `trans_email/ident_general/email` |  | | | 敏感 |
| 发件人姓名 | `trans_email/ident_sales/name` |  | | | 敏感 |
| 发件人电子邮件 | `trans_email/ident_sales/email` |  | | | 敏感 |
| 发件人姓名 | `trans_email/ident_support/name` |  | | | 敏感 |
| 发件人电子邮件 | `trans_email/ident_support/email` |  | | | 敏感 |
| 发件人姓名 | `trans_email/ident_custom1/name` |  | | | 敏感 |
| 发件人电子邮件 | `trans_email/ident_custom1/email` |  | | | 敏感 |
| 发件人姓名 | `trans_email/ident_custom2/name` |  | | | 敏感 |
| 发件人电子邮件 | `trans_email/ident_custom2/email` |  | | | 敏感 |

{style="table-layout:auto"}

### 联系人敏感路径和系统特定路径

这些配置值在&#x200B;**存储** >设置> **配置** > **常规** > **联系人**&#x200B;中的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 发送电子邮件至 | `contact/email/recipient_email` |  | | | 敏感 |
| 电子邮件发件人 | `contact/email/sender_email_identity` |  | | | 敏感 |
| 电子邮件模板 | `contact/email/email_template` |  | | | 敏感 |

{style="table-layout:auto"}

### New Relic报表敏感路径和系统特定路径

这些配置值在&#x200B;**存储** >设置> **配置** > **常规** > **New Relic报表**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic帐户ID | `newrelicreporting/general/account_id` |  | | | 敏感 |
| New Relic应用程序ID | `newrelicreporting/general/app_id` |  | | | 敏感 |
| New Relic API密钥 | `newrelicreporting/general/api` |  | 已加密 | | 敏感 |
| 分析API密钥 | `newrelicreporting/general/insights_insert_key` |  | 已加密 | | 敏感 |
| NEW RELIC API URL | `newrelicreporting/general/api_url` |  | | 系统特定 | 敏感 |
| 分析API URL | `newrelicreporting/general/insights_api_url` |  | | 系统特定 | 敏感 |

{style="table-layout:auto"}

## 客户区分类别和特定于系统的路径

此部分列出了&#x200B;**商店** >设置> **配置** > **客户**&#x200B;下的管理员中选项可用的变量名称和配置路径。

### 区分客户配置和特定于系统的路径

这些配置值在&#x200B;**商店** >设置> **配置** > **客户** > **客户配置**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 默认电子邮件域 | `customer/create_account/email_domain` |  | | 系统特定 | |

{style="table-layout:auto"}

## 目录类别

此部分列出了&#x200B;**商店** >设置> **配置** > **目录**&#x200B;下的管理员中选项可用的变量名称和配置路径。

### 目录敏感路径和系统特定路径

这些配置值在&#x200B;**存储** >设置> **配置** > **目录** > **目录**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 错误电子邮件收件人 | `catalog/productalert_cron/error_email` |  | | | 敏感 |
| YouTube API密钥 | `catalog/product_video/youtube_api_key` |  | | | 敏感 |
| Solr服务器主机名 | `catalog/search/solr_server_hostname` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| Solr服务器端口 | `catalog/search/solr_server_port` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| Solr服务器用户名 | `catalog/search/solr_server_username` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| Solr服务器密码 | `catalog/search/solr_server_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| Solr服务器路径 | `catalog/search/solr_server_path` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| Elasticsearch服务器主机名 | `catalog/search/elasticsearch_server_hostname` |  | | 系统特定 | 敏感 |
| Elasticsearch服务器端口 | `catalog/search/elasticsearch_server_port` |  | | 系统特定 | 敏感 |
| Elasticsearch索引前缀 | `catalog/search/elasticsearch_index_prefix` |  | | 系统特定 | 敏感 |
| 启用Elasticsearch HTTP身份验证 | `catalog/search/elasticsearch_enable_auth` |  | | 系统特定 | |
| Elasticsearch HTTP用户名 | `catalog/search/elasticsearch_username` |  | | 系统特定 | |
| Elasticsearch HTTP密码 | `catalog/search/elasticsearch_password` |  | | 系统特定 | |
| Elasticsearch Server Timeout | `catalog/search/elasticsearch_server_timeout` |  | | 系统特定 | |
| Elasticsearch HTTP用户名 | `catalog/search/elasticsearch_username` | | | 系统特定 | |
| Elasticsearch HTTP密码 | `catalog/search/elasticsearch_password` | | | 系统特定 | |
| Elasticsearch Server Timeout | `catalog/search/elasticsearch_server_timeout` | | | 系统特定 | |
| OpenSearch服务器主机名 | `catalog/search/opensearch_server_hostname` | | | 系统特定 | 敏感 |
| OpenSearch服务器端口 | `catalog/search/opensearch_server_port` | | | 系统特定 | 敏感 |
| OpenSearch索引前缀 | `catalog/search/opensearch_index_prefix` | | | 系统特定 | 敏感 |
| 启用OpenSearch HTTP身份验证 | `catalog/search/opensearch_enable_auth` | | | 系统特定 | |
| OpenSearch HTTP用户名 | `catalog/search/opensearch_username` | | | 系统特定 | |
| OpenSearch HTTP密码 | `catalog/search/opensearch_password` | | | 系统特定 | |
| OpenSearch服务器超时 | `catalog/search/opensearch_server_timeout` | | | 系统特定 | |

{style="table-layout:auto"}

>[!NOTE]
>
>Adobe Commerce 2.4.6中引入了OpenSearch设置。

### 清点敏感路径和系统特定路径

这些配置值在&#x200B;**存储** >设置> **配置** > **目录** > **清单**&#x200B;中的管理员中可用。

|名称|配置路径| Commerce版本支持|是否加密？ |系统特定？ |敏感？ | |
&#x200B;------------------------------------------ ----------------------------
| Google API密钥| `cataloginventory/source_selection_distance_based_google/api_key` ||加密| |敏感|

### XML Sitemap敏感路径和系统特定路径

这些配置值在&#x200B;**存储** >设置> **配置** > **目录** > **XML Sitemap**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 错误电子邮件收件人 | `sitemap/generate/error_email` |  | | | 敏感 |

{style="table-layout:auto"}

## 销售类别

此部分列出了&#x200B;**商店** >设置> **配置** > **销售**&#x200B;下的管理员中选项可用的变量名称和配置路径。

### 运输设置敏感且特定于系统的路径

这些配置值在&#x200B;**商店** >设置> **配置** > **销售** > **配送设置**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 国家/地区 | `shipping/origin/country_id` |  | | | 敏感 |
| 地区/州 | `shipping/origin/region_id` |  | | | 敏感 |
| 邮政编码 | `shipping/origin/postcode` |  | | | 敏感 |
| 城市 | `shipping/origin/city` |  | | | 敏感 |
| 街道地址 | `shipping/origin/street_line1` |  | | | 敏感 |
| 街道地址行2 | `shipping/origin/street_line2` |  | | | 敏感 |
| 实时帐户 | `carriers/ups/is_account_live` |  | | 系统特定 | |

{style="table-layout:auto"}

### 销售电子邮件敏感路径和系统特定路径

这些配置值在&#x200B;**商店** >设置> **配置** > **销售** > **销售电子邮件**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 将订单电子邮件副本发送至 | `sales_email/order/copy_to` |  | | | 敏感 |
| 将订单注释电子邮件副本发送至 | `sales_email/order_comment/copy_to` |  | | | 敏感 |
| 将发票电子邮件副本发送至 | `sales_email/invoice/copy_to` |  | | | 敏感 |
| 将发票注释电子邮件副本发送至 | `sales_email/invoice_comment/copy_to` |  | | | 敏感 |
| 将装运电子邮件副本发送至 | `sales_email/shipment/copy_to` |  | | | 敏感 |
| 将装运注释电子邮件副本发送至 | `sales_email/shipment_comment/copy_to` |  | | | 敏感 |
| 将贷项通知单电子邮件副本发送至 | `sales_email/creditmemo/copy_to` |  | | | 敏感 |
| 将贷项通知单注释电子邮件副本发送至 | `sales_email/creditmemo_comment/copy_to` |  | | | 敏感 |
| 将取车准备电子邮件副本发送至 | `sales_email/temando_pickup/copy_to` |  | | | 敏感 |

{style="table-layout:auto"}

### 签出敏感路径和特定于系统的路径

这些配置值在&#x200B;**商店** >设置> **配置** > **销售** > **结帐**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 将付款失败电子邮件副本发送至 | `checkout/payment_failed/copy_to` |  | | | 敏感 |

{style="table-layout:auto"}

### Google API敏感路径和系统特定路径

这些配置值在&#x200B;**商店** >设置> **配置** > **销售** > **Google API**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 容器ID | `google/analytics/container_id` | 仅限Commerce Enterprise | | | 敏感 |

{style="table-layout:auto"}

### 敏感和系统特定路径的投放方法

这些配置值在&#x200B;**商店** >设置> **配置** > **销售** > **交付方法**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 网关URL | `carriers/usps/gateway_url` |  | | | 敏感 |
| 安全网关URL | `carriers/usps/gateway_secure_url` |  | | | 敏感 |
| 标题 | `carriers/usps/title` |  | | | |
| 用户 ID | `carriers/usps/userid` |  | 已加密 | | 敏感 |
| 密码 | `carriers/usps/password` |  | 已加密 | | 敏感 |
| 用户 ID | `carriers/ups/username` |  | 已加密 | | 敏感 |
| 密码 | `carriers/ups/password` |  | 已加密 | | 敏感 |
| 访问许可证编号 | `carriers/ups/access_license_number` |  | 已加密 | | 敏感 |
| 跟踪XML URL | `carriers/ups/tracking_xml_url` |  | | | 敏感 |
| 网关XML URL | `carriers/ups/gateway_xml_url` |  | | | 敏感 |
| 发货人编号 | `carriers/ups/shipper_number` |  | | | 敏感 |
| 调试 | `carriers/ups/debug` |  | | | 敏感 |
| 帐户 ID | `carriers/fedex/account` |  | 已加密 | | 敏感 |
| 键 | `carriers/fedex/key` |  | 已加密 | | 敏感 |
| 计量器编号 | `carriers/fedex/meter_number` |  | 已加密 | | 敏感 |
| 密码 | `carriers/fedex/password` |  | 已加密 | | 敏感 |
| 访问ID | `carriers/dhl/id` |  | 已加密 | | 敏感 |
| 密码 | `carriers/dhl/password` |  | 已加密 | | 敏感 |
| 调试 | `carriers/dhl/debug` |  | | | |
| 帐号 | `carriers/dhl/account` |  | | | 敏感 |
| 网关URL | `carriers/dhl/gateway_url` |  | | | 敏感 |
| 沙盒模式 | `carriers/fedex/sandbox_mode` |  | | | 敏感 |

{style="table-layout:auto"}

### 对销售敏感且特定于系统的路径

这些配置值在&#x200B;**商店** >设置> **配置** > **销售** > **销售**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 联系人姓名 | `sales/magento_rma/store_name` | 仅限Commerce Enterprise | | | 敏感 |
| 街道地址 | `sales/magento_rma/address` | 仅限Commerce Enterprise | | | 敏感 |
| 街道地址 | `sales/magento_rma/address1` |  | | | 敏感 |
| 城市 | `sales/magento_rma/city` | 仅限Commerce Enterprise | | | 敏感 |
| 省/市/自治区 | `sales/magento_rma/region_id` | 仅限Commerce Enterprise | | | 敏感 |
| 邮政编码 | `sales/magento_rma/zip` | 仅限Commerce Enterprise | | | 敏感 |
| 国家/地区 | `sales/magento_rma/country_id` | 仅限Commerce Enterprise | | | 敏感 |
| 将RMA电子邮件副本发送至 | `sales_email/magento_rma/copy_to` | 仅限Commerce Enterprise | | | 敏感 |
| 发送RMA授权电子邮件副本至 | `sales_email/magento_rma_auth/copy_to` | 仅限Commerce Enterprise | | | 敏感 |
| 发送RMA备注电子邮件副本至 | `sales_email/magento_rma_comment/copy_to` | 仅限Commerce Enterprise | | | 敏感 |
| 发送RMA备注电子邮件副本至 | `sales_email/magento_rma_customer_comment/copy_to` | 仅限Commerce Enterprise | | | 敏感 |

{style="table-layout:auto"}

### Google API路径

这些配置值在&#x200B;**商店** >设置> **配置** > **销售** > **Google API**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 帐号 | `google/analytics/account` |  | | | 敏感 |

{style="table-layout:auto"}

## 高级类别

此部分列出了&#x200B;**商店** >设置> **配置** > **高级**&#x200B;下的管理员中选项可用的变量名称和配置路径。

### 区分管理员和特定于系统的路径

这些配置值在&#x200B;**存储** >设置> **配置** > **高级** > **管理员**&#x200B;中的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 自定义管理员URL | `admin/url/custom` |  | | | 敏感 |
| 自定义管理路径 | `admin/url/custom_path` |  | | | 敏感 |

{style="table-layout:auto"}

### 系统敏感路径和系统特定路径

这些配置值在&#x200B;**存储** >设置> **配置** > **高级** > **系统**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 错误电子邮件收件人 | `system/magento_scheduled_import_export_log/error_email` |  | | | 敏感 |
| 访问列表 | `system/full_page_cache/varnish/access_list` |  |  | | 敏感 |
| 错误电子邮件发件人 | `system/magento_scheduled_import_export_log/error_email_identity` |  |  | | 敏感 |

{style="table-layout:auto"}

### 开发人员敏感路径和系统特定路径

这些配置值在&#x200B;**商店** >设置> **配置** > **高级** > **开发人员**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 允许的IP（逗号分隔） | `dev/restrict/allow_ips` |  | | 系统特定 | 敏感 |

{style="table-layout:auto"}

## 高级类别

此部分列出了&#x200B;**商店** >设置> **配置** > **高级**&#x200B;下的管理员中选项可用的变量名称和配置路径。

### 系统路径

这些配置值在&#x200B;**存储** >设置> **配置** > **高级** > **系统**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 主机 | `system/smtp/host` |  | | 系统特定 | 敏感 |
| 端口(25) | `system/smtp/port` |  | | 系统特定 | 敏感 |
| 后端主机 | `system/full_page_cache/varnish/backend_host` |  | | 系统特定 | 敏感 |
| 后端端口 | `system/full_page_cache/varnish/backend_port` |  | | 系统特定 | 敏感 |

{style="table-layout:auto"}

### 开发人员路径

这些配置值在&#x200B;**商店** >设置> **配置** > **高级** > **开发人员**&#x200B;的管理员中可用。

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 将JS错误记录到会话存储密钥 | `dev/js/session_storage_key` | ![不仅Commerce](/help/assets/configuration/red-x.png) | | 系统特定 | |

{style="table-layout:auto"}

## 支付敏感和系统特定的路径

此部分列出了&#x200B;**商店** >设置> **配置** > **销售** > **付款**&#x200B;下的管理员中选项可用的变量名称和配置路径。

### 常规变量

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ |
|--------------|--------------|--------------|--------------|
| 商家所在国家/地区 | `paypal/general/merchant_country` |  | 敏感 |

{style="table-layout:auto"}

>[!INFO]
>
>您对此变量的选择决定了您可以使用哪些[国际路径](#international-paths)。

### PayPal敏感路径和系统特定路径

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 与PayPal商家帐户关联的电子邮件（可选） | `paypal/general/business_account` |  | | | 敏感 |
| 商家帐户ID | `payment/paypal_express/merchant_id` |  | | | 敏感 |
| 发布者ID | `payment/paypal_express_bml/publisher_id` |  | | | 敏感 |
| 密码 | `paypal/fetch_reports/ftp_password` |  | 已加密 | | 敏感 |
| 登录 | `paypal/fetch_reports/ftp_login` |  | 已加密 | | 敏感 |
| 自定义端点主机名或IP地址 | `paypal/fetch_reports/ftp_ip` |  | | 系统特定 | 敏感 |
| 沙盒模式 | `paypal/fetch_reports/ftp_sandbox` |  | | 系统特定 | |
| 调试模式 | `payment/paypal_express/debug` |  | | 系统特定 | |
| 调试模式 | `payment/paypal_billing_agreement/debug` |  | | 系统特定 | |
| SFTP凭据 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |

{style="table-layout:auto"}

### PayPal Payflow Pro敏感路径和系统特定路径

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 用户 | `payment/payflow_advanced/user` |  | 已加密 | | 敏感 |
| 密码 | `payment/payflow_advanced/pwd` |  | 已加密 | | 敏感 |
| 自定义路径 | `paypal/fetch_reports/ftp_path` |  | | 系统特定 | 敏感 |
| 用户 | `payment/payflowpro/user` |  | 已加密 | | 敏感 |
| 密码 | `payment/payflowpro/pwd` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment/payflowpro/sandbox_flag` |  | | 系统特定 | |
| 合作伙伴 | `payment/payflowpro/partner` |  | | | 敏感 |
| 代理主机 | `payment/payflowpro/proxy_host` |  | | 系统特定 | 敏感 |
| 代理端口 | `payment/payflowpro/proxy_port` |  | | 系统特定 | 敏感 |
| 调试模式 | `payment/payflowpro/debug` |  | | 系统特定 | |
| SFTP凭据 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | 系统特定 | |
| 信用卡设置 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` |  | | | 敏感 |

{style="table-layout:auto"}

### PayPal Payflow链接敏感路径和系统特定路径

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 用户 | `payment/payflow_link/user` |  | 已加密 | | 敏感 |
| 密码 | `payment/payflow_link/pwd` |  | 已加密 | | 敏感 |
| 测试模式 | `payment/payflow_link/sandbox_flag` |  | | 系统特定 | |
| 使用代理 | `payment/payflow_link/use_proxy` |  | | 系统特定 | |
| 代理主机 | `payment/payflow_link/proxy_host` |  | | 系统特定 | |
| 代理端口 | `payment/payflow_link/proxy_port` |  |  | 系统特定 | |
| 调试模式 | `payment/payflow_link/debug` |  | | 系统特定 | |
| 用于取消URL和返回URL的URL方法 | `payment/payflow_link/url_method` |  | | 系统特定 | |
| 调试模式 | `payment/payflow_express/debug` |  | | 系统特定 | |
| SFTP凭据 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 敏感 |

{style="table-layout:auto"}

### PayPal Payments Pro敏感且特定于系统的路径

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API用户名 | `paypal/wpp/api_username` |  | 已加密 | | 敏感 |
| API密码 | `paypal/wpp/api_password` |  | 已加密 | | 敏感 |
| API签名 | `paypal/wpp/api_signature` |  | 已加密 | | 敏感 |
| API证书 | `paypal/wpp/api_cert` |  | | | 敏感 |
| 代理主机 | `paypal/wpp/proxy_host` |  | | 系统特定 | 敏感 |
| 代理端口 | `paypal/wpp/proxy_port` |  | | 系统特定 | 敏感 |
| 沙盒模式 | `paypal/wpp/sandbox_flag` |  | | 系统特定 | |
| SFTP凭据 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |

{style="table-layout:auto"}

### PayPal Payments Pro托管敏感且特定于系统的路径

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 调试模式 | `payment/hosted_pro/debug` |  | | 系统特定 | |
| SFTP凭据 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |

{style="table-layout:auto"}

### Braintree敏感路径和系统特定路径

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 商家ID | `payment/braintree/merchant_id` |  | | | 敏感 |
| 公共密钥 | `payment/braintree/public_key` |  | 已加密 | | 敏感 |
| 私钥 | `payment/braintree/private_key` |  | 已加密 | | 敏感 |
| 商家帐户ID | `payment/braintree/merchant_account_id` |  | | | 敏感 |
| Kount Merchant ID | `payment/braintree/kount_id` |  | | | 敏感 |
| 覆盖商家名称 | `payment/braintree_paypal/merchant_name_override` |  | | | 敏感 |
| 电话 | `payment/braintree/descriptor_phone` |  | | | 敏感 |
| URL | `payment/braintree/descriptor_url` |  | | 系统特定 | |

{style="table-layout:auto"}

### 支票/汇票路径

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 发送支票到 | `payment/checkmo/mailing_address` |  | | | 敏感 |
| 发送支票到 | `payment_us/checkmo/mailing_address` |  | | | 敏感 |

{style="table-layout:auto"}

### 国际路径

| 名称 | 配置路径 | Commerce版本支持 | 是否加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 交易密钥 | `payment_au/authorizenet_directpost/trans_key` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_au/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_au/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_au/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 交易密钥 | `payment_au/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 访问密钥 | `payment_au/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 密钥 | `payment_au/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_au/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 付款响应密码 | `payment_au/worldpay/response_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 远程管理员授权密码 | `payment_au/worldpay/auth_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 沙盒模式 | `payment_au/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_au/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_au/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_au/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_au/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密码 | `payment_au/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_au/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 交易密钥 | `payment_es/authorizenet_directpost/trans_key` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_es/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_es/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_es/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 交易密钥 | `payment_es/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 访问密钥 | `payment_es/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 密钥 | `payment_es/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_es/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 付款响应密码 | `payment_es/worldpay/response_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 远程管理员授权密码 | `payment_es/worldpay/auth_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 交易的MD5密码 | `payment_es/worldpay/md5_secret` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 调试 | `payment_es/worldpay/debug` | 仅限Commerce Enterprise | | 系统特定 | |
| 沙盒模式 | `payment_es/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_es/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_es/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_es/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_es/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密码 | `payment_es/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_es/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 交易密钥 | `payment_nz/authorizenet_directpost/trans_key` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_nz/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_nz/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_nz/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 测试模式 | `payment_nz/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 测试模式 | `payment_nz/worldpay/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 沙盒模式 | `payment_nz/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_nz/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_nz/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_nz/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_nz/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 沙盒API密码 | `payment_nz/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_nz/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment/payflow_advanced/sandbox_flag` |  | | 系统特定 | |
| 代理主机 | `payment/payflow_advanced/proxy_host` |  | | 系统特定 | 敏感 |
| 代理端口 | `payment/payflow_advanced/proxy_port` |  | | 系统特定 | |
| 调试模式 | `payment/payflow_advanced/debug` |  | | 系统特定 | |
| 用于取消URL和返回URL的URL方法 | `payment/payflow_advanced/url_method` |  | | 系统特定 | |
| 测试模式 | `payment_us/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_us/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_us/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 访问密钥 | `payment_us/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 密钥 | `payment_us/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_us/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 测试模式 | `payment_us/worldpay/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 沙盒模式 | `payment_us/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_us/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_us/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_us/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_us/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密码 | `payment_us/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_us/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | |
| 测试模式 | `payment_gb/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 测试模式 | `payment_gb/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_gb/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_gb/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 测试模式 | `payment_gb/worldpay/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 沙盒模式 | `payment_gb/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_gb/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_gb/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_gb/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_gb/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密码 | `payment_gb/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_gb/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 交易密钥 | `payment_de/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 访问密钥 | `payment_de/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 密钥 | `payment_de/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_de/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 交易密钥 | `payment_de/authorizenet_directpost/trans_key` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_de/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_de/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_de/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 付款响应密码 | `payment_de/worldpay/response_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 远程管理员授权密码 | `payment_de/worldpay/auth_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 调试 | `payment_de/worldpay/debug` | 仅限Commerce Enterprise | | 系统特定 | |
| 沙盒模式 | `payment_de/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_de/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_de/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_de/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_de/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密码 | `payment_de/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_de/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 交易密钥 | `payment_other/authorizenet_directpost/trans_key` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_other/authorizenet_directpost/test` |  | | 系统特定 | 敏感 |
| 网关URL | `payment_other/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_other/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | |
| 交易密钥 | `payment_other/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 访问密钥 | `payment_other/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 密钥 | `payment_other/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 新订单状态 | `payment_other/cybersource/order_status` | 仅限Commerce Enterprise | | 系统特定 | |
| 测试模式 | `payment_other/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 付款响应密码 | `payment_other/worldpay/response_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 远程管理员授权密码 | `payment_other/worldpay/auth_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 测试模式 | `payment_other/worldpay/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 沙盒模式 | `payment_other/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_other/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_other/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_other/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_other/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密码 | `payment_other/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_other/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 交易密钥 | `payment_ca/authorizenet_directpost/trans_key` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_ca/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_ca/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_ca/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 交易密钥 | `payment_ca/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 访问密钥 | `payment_ca/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 密钥 | `payment_ca/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 新订单状态 | `payment_ca/cybersource/order_status` | 仅限Commerce Enterprise | | | |
| 测试模式 | `payment_ca/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 付款响应密码 | `payment_ca/worldpay/response_password` | 仅限Commerce Enterprise | | 系统特定 | |
| 远程管理员授权密码 | `payment_ca/worldpay/auth_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 测试模式 | `payment_ca/worldpay/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 沙盒模式 | `payment_ca/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_ca/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_ca/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_ca/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_ca/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 沙盒API密码 | `payment_ca/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_ca/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 交易密钥 | `payment_hk/authorizenet_directpost/trans_key` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_hk/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_hk/authorizenet_directpost/cgi_url` |  | | | 敏感 |
| 交易详细信息URL | `payment_hk/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 交易密钥 | `payment_hk/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 访问密钥 | `payment_hk/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 密钥 | `payment_hk/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_hk/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 付款响应密码 | `payment_hk/worldpay/response_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 远程管理员授权密码 | `payment_hk/worldpay/auth_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 测试模式 | `payment_hk/worldpay/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 实时API密钥 | `payment_hk/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 实时API密码 | `payment_hk/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_hk/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_hk/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密码 | `payment_hk/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_hk/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 交易密钥 | `payment_jp/authorizenet_directpost/trans_key` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_jp/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_jp/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_jp/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 交易密钥 | `payment_jp/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 访问密钥 | `payment_jp/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 密钥 | `payment_jp/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 新订单状态 | `payment_jp/cybersource/order_status` | 仅限Commerce Enterprise | | 系统特定 | |
| 测试模式 | `payment_jp/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 付款响应密码 | `payment_jp/worldpay/response_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 远程管理员授权密码 | `payment_jp/worldpay/auth_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 测试模式 | `payment_jp/worldpay/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 沙盒模式 | `payment_jp/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_jp/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_jp/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_jp/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_jp/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密码 | `payment_jp/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_jp/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 交易密钥 | `payment_fr/authorizenet_directpost/trans_key` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_fr/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_fr/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_fr/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 交易密钥 | `payment_fr/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 访问密钥 | `payment_fr/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 密钥 | `payment_fr/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_fr/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 付款响应密码 | `payment_fr/worldpay/response_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 远程管理员授权密码 | `payment_fr/worldpay/auth_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 测试模式 | `payment_fr/worldpay/sandbox_flag` | 仅限Commerce Enterprise |  | 系统特定 | |
| 沙盒模式 | `payment_fr/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_fr/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_fr/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_fr/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_fr/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密码 | `payment_fr/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_fr/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 交易密钥 | `payment_it/authorizenet_directpost/trans_key` |  | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_it/authorizenet_directpost/test` |  | | 系统特定 | |
| 网关URL | `payment_it/authorizenet_directpost/cgi_url` |  | | 系统特定 | 敏感 |
| 交易详细信息URL | `payment_it/authorizenet_directpost/cgi_url_td` |  | | 系统特定 | 敏感 |
| 交易密钥 | `payment_it/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 访问密钥 | `payment_it/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 密钥 | `payment_it/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 测试模式 | `payment_it/cybersource/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 付款响应密码 | `payment_it/worldpay/response_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 远程管理员授权密码 | `payment_it/worldpay/auth_password` | 仅限Commerce Enterprise | | 系统特定 | 敏感 |
| 测试模式 | `payment_it/worldpay/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 沙盒模式 | `payment_it/eway/sandbox_flag` | 仅限Commerce Enterprise | | 系统特定 | |
| 实时API密钥 | `payment_it/eway/live_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时API密码 | `payment_it/eway/live_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 实时客户端加密密钥 | `payment_it/eway/live_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密钥 | `payment_it/eway/sandbox_api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒API密码 | `payment_it/eway/sandbox_api_password` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| 沙盒客户端加密密钥 | `payment_it/eway/sandbox_encryption_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| API密钥 | `fraud_protection/signifyd/api_key` | 仅限Commerce Enterprise | 已加密 | 系统特定 | 敏感 |
| API URL | `fraud_protection/signifyd/api_url` | 仅限Commerce Enterprise |  | 系统特定 | 敏感 |
| SFTP凭据 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| API登录ID | `payment_au/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_au/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 向客户发送电子邮件 | `payment_au/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_au/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 远程管理员安装ID | `payment_au/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密码 | `payment_au/worldpay/md5_secret` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 发送支票到 | `payment_es/checkmo/mailing_address` |  | | | 敏感 |
| API登录ID | `payment_es/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_es/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 向客户发送电子邮件 | `payment_es/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_es/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_es/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_es/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 远程管理员安装ID | `payment_es/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | | | | | |
| SFTP凭据 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| API登录ID | `payment_nz/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_nz/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 向客户发送电子邮件 | `payment_nz/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_nz/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_nz/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 交易密钥 | `payment_nz/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_nz/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 访问密钥 | `payment_nz/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 密钥 | `payment_nz/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 安装Id | `payment_nz/worldpay/installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 付款响应密码 | `payment_nz/worldpay/response_password` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员安装ID | `payment_nz/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员授权密码 | `payment_nz/worldpay/auth_password` | 仅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密码 | `payment_nz/worldpay/md5_secret` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 敏感 |
| API登录ID | `payment_us/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 交易密钥 | `payment_us/authorizenet_directpost/trans_key` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_us/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 向客户发送电子邮件 | `payment_us/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_us/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_us/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 交易密钥 | `payment_us/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_us/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 安装Id | `payment_us/worldpay/installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 付款响应密码 | `payment_us/worldpay/response_password` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员安装ID | `payment_us/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员授权密码 | `payment_us/worldpay/auth_password` | 仅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密码 | `payment_us/worldpay/md5_secret` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | 敏感 |
| SFTP凭据 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 发送支票到 | `payment_gb/checkmo/mailing_address` |  | | | 敏感 |
| 商家ID | `payment_gb/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 交易密钥 | `payment_gb/cybersource/transaction_key` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_gb/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 访问密钥 | `payment_gb/cybersource/access_key` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 密钥 | `payment_gb/cybersource/secret_key` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| API登录ID | `payment_gb/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 交易密钥 | `payment_gb/authorizenet_directpost/trans_key` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_gb/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 向客户发送电子邮件 | `payment_gb/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_gb/authorizenet_directpost/merchant_email` |  |  | | 敏感 |
| 安装Id | `payment_gb/worldpay/installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 付款响应密码 | `payment_gb/worldpay/response_password` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员安装ID | `payment_gb/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员授权密码 | `payment_gb/worldpay/auth_password` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 将支票支付给 | `payment_de/checkmo/payable_to` |  | | | 敏感 |
| 发送支票到 | `payment_de/checkmo/mailing_address` |  | | | 敏感 |
| 商家ID | `payment_de/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_de/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| API登录ID | `payment_de/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_de/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 向客户发送电子邮件 | `payment_de/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_de/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 安装Id | `payment_de/worldpay/installation_id` | 仅限Commerce Enterprise | | | |
| 远程管理员安装ID | `payment_de/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密码 | `payment_de/worldpay/md5_secret` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | 敏感 |
| SFTP凭据 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 将支票支付给 | `payment_other/checkmo/payable_to` |  | | | 敏感 |
| 发送支票到 | `payment_other/checkmo/mailing_address` |  | | | 敏感 |
| API登录ID | `payment_other/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_other/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 新订单状态 | `payment_other/authorizenet_directpost/order_status` |  | | | 敏感 |
| 商户电子邮件 | `payment_other/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_other/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_other/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 安装Id | `payment_other/worldpay/installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员安装ID | `payment_other/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密码 | `payment_other/worldpay/md5_secret` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 敏感 |
| 将支票支付给 | `payment_ca/checkmo/payable_to` |  | | | 敏感 |
| 发送支票到 | `payment_ca/checkmo/mailing_address` |  | | | 敏感 |
| API登录ID | `payment_ca/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_ca/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 新订单状态 | `payment_ca/authorizenet_directpost/order_status` |  | | | 敏感 |
| 向客户发送电子邮件 | `payment_ca/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_ca/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_ca/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_ca/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 安装Id | `payment_ca/worldpay/installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员安装ID | `payment_ca/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密码 | `payment_ca/worldpay/md5_secret` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  |  | | 敏感 |
| SFTP凭据 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 将支票支付给 | `payment_hk/checkmo/payable_to` |  | | | 敏感 |
| 发送支票到 | `payment_hk/checkmo/mailing_address` |  | | | 敏感 |
| API登录ID | `payment_hk/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_hk/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 向客户发送电子邮件 | `payment_hk/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_hk/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_hk/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_hk/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 安装Id | `payment_hk/worldpay/installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员安装ID | `payment_hk/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密码 | `payment_hk/worldpay/md5_secret` | 仅限Commerce Enterprise | | | 敏感 |
| 签名字段 | `payment_hk/worldpay/signature_fields` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 将支票支付给 | `payment_jp/checkmo/payable_to` |  | | | 敏感 |
| 发送支票到 | `payment_jp/checkmo/mailing_address` |  | | | 敏感 |
| API登录ID | `payment_jp/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_jp/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 向客户发送电子邮件 | `payment_jp/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_jp/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_jp/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_jp/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 安装Id | `payment_jp/worldpay/installation_id` | 仅限Commerce Enterprise | | | |
| 远程管理员安装ID | `payment_jp/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密码 | `payment_jp/worldpay/md5_secret` | 仅限Commerce Enterprise | | | 敏感 |
| 签名字段 | `payment_jp/worldpay/signature_fields` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 将支票支付给 | `payment_fr/checkmo/payable_to` |  | | | 敏感 |
| 发送支票到 | `payment_fr/checkmo/mailing_address` |  | | | 敏感 |
| API登录ID | `payment_fr/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_fr/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 向客户发送电子邮件 | `payment_fr/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_fr/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_fr/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_fr/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 安装Id | `payment_fr/worldpay/installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员安装ID | `payment_fr/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密码 | `payment_fr/worldpay/md5_secret` | 仅限Commerce Enterprise | | | 敏感 |
| 签名字段 | `payment_fr/worldpay/signature_fields` | 仅限Commerce Enterprise | | | 敏感 |
| SFTP凭据 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 敏感 |
| SFTP凭据 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 敏感 |
| 将支票支付给 | `payment_it/checkmo/payable_to` |  | | | 敏感 |
| 发送支票到 | `payment_it/checkmo/mailing_address` |  | | | 敏感 |
| API登录ID | `payment_it/authorizenet_directpost/login` |  | 已加密 | | 敏感 |
| 商家MD5 | `payment_it/authorizenet_directpost/trans_md5` |  | 已加密 | | 敏感 |
| 向客户发送电子邮件 | `payment_it/authorizenet_directpost/email_customer` |  | | | 敏感 |
| 商户电子邮件 | `payment_it/authorizenet_directpost/merchant_email` |  | | | 敏感 |
| 商家ID | `payment_it/cybersource/merchant_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 配置文件ID | `payment_it/cybersource/profile_id` | 仅限Commerce Enterprise | 已加密 | | 敏感 |
| 安装Id | `payment_it/worldpay/installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 远程管理员安装ID | `payment_it/worldpay/admin_installation_id` | 仅限Commerce Enterprise | | | 敏感 |
| 交易的MD5密码 | `payment_it/worldpay/md5_secret` | 仅限Commerce Enterprise | | | 敏感 |

{style="table-layout:auto"}
