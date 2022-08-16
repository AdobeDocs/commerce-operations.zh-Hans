---
title: 敏感和特定于系统的路径
description: 请参阅特定于系统的敏感配置值列表。
source-git-commit: 019d638403f2dc3e170a56842335da203126d8a6
workflow-type: tm+mt
source-wordcount: '3711'
ht-degree: 0%

---


# 敏感和系统特定的设置

本主题列出了特定于系统和敏感设置的配置路径：

- 的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 将特定于系统的设置写入特定于系统的配置文件， `app/etc/env.php`，应为 _not_ 在源代码管理中。 它还会将所有Commerce实例的共享配置写入 `app/etc/config.php`，此文件 _show_ 在源代码管理中。
- 的 [`magento config:sensitive:set` 命令](../cli/set-configuration-values.md) 将敏感设置写入 `app/etc/env.php`.

   您还可以使用配置变量设置敏感值，如 [使用环境变量覆盖配置设置](../reference/override-config-settings.md#environment-variables).

有关其他配置路径的列表，请参阅：

- [除付款外的所有配置路径](../reference/config-reference-general.md)
- [付款配置路径](../reference/config-reference-payment.md).

>[!INFO]
>
>本主题中列出的所有配置路径都是敏感的。 的 `System-specific?` 列会显示哪些值也特定于系统。

## 一般类别敏感路径和特定于系统的路径

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **常规**.

### Web路径敏感且特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **常规** > **Web**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 基本URL | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 基本链接URL | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 静态视图文件的基本URL | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 用户媒体文件的基本URL | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 安全基本URL | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 安全基本链接URL | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 静态视图文件的安全基本URL | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 用户媒体文件的安全基本URL | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 默认Web URL | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 默认无路由URL | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| Cookie路径 | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| Cookie域 | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| Cookie生命周期 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 仅使用HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| Cookie限制模式 | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### 货币设置敏感路径和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **常规** > **货币设置**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 错误电子邮件收件人 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 存储对电子邮件地址敏感且特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **电子邮件配置** > **常规** > **存储电子邮件地址**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 发件人名称 | `trans_email/ident_general/name` |  |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发件人电子邮件 | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发件人名称 | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发件人电子邮件 | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发件人名称 | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发件人电子邮件 | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发件人名称 | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发件人电子邮件 | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发件人名称 | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发件人电子邮件 | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 联系人敏感和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **常规** > **联系人**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 向发送电子邮件 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件发件人 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件模板 | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 新的Relic报告敏感且特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **常规** > **New Relic报表**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 新旧帐户ID | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| New Relic Application ID | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| New Relic API密钥 | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 分析API密钥 | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新建Relic API URL | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 分析API URL | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## 客户类别敏感且特定于系统的路径

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **客户**.

### 对客户配置敏感且特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **客户** > **客户配置**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 默认电子邮件域 | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

## 目录类别

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **目录**.

### 目录敏感路径和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **目录** > **目录**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 错误电子邮件收件人 | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| YouTube API密钥 | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr服务器主机名 | `catalog/search/solr_server_hostname` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr服务器端口 | `catalog/search/solr_server_port` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr服务器用户名 | `catalog/search/solr_server_username` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr服务器密码 | `catalog/search/solr_server_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Solr服务器路径 | `catalog/search/solr_server_path` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch服务器主机名 | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch服务器端口 | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch索引前缀 | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 启用ElasticsearchHTTP身份验证 | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP用户名 | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP密码 | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| Elasticsearch服务器超时 | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### 清单敏感路径和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **目录** > **库存**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Google API密钥 | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### XML站点地图敏感路径和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **目录** > **XML站点地图**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 错误电子邮件收件人 | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## 销售类别

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **销售**.

### 发运设置敏感路径和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **装运设置**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 国家/地区 | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 地区/州 | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 邮政编码 | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 城市 | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址2号线 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时帐户 | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### 对销售电子邮件敏感且特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **销售电子邮件**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 将订单电子邮件副本发送到 | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将订单评论电子邮件副本发送到 | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将发票电子邮件副本发送到 | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将发票评论电子邮件副本发送到 | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将发运电子邮件副本发送到 | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将发运评论电子邮件副本发送到 | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将贷项通知单电子邮件副本发送到 | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将贷项通知单评论电子邮件副本发送到 | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将“装货准备”电子邮件副本发送到 | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 结账敏感路径和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **结帐**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 将付款失败的电子邮件副本发送到 | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Google API敏感路径和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **Google API**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 容器Id | `google/analytics/container_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 传送方法敏感路径和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **投放方法**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 网关URL | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安全网关URL | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 标题 | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 用户ID | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密码 | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 用户ID | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密码 | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问许可证号 | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 跟踪XML URL | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 网关XML URL | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发货人编号 | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 调试 | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 帐户ID | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 键 | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 仪表号 | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密码 | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问ID | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密码 | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 调试 | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 帐号 | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 网关URL | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒模式 | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 销售敏感型路径和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **销售**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 联系人姓名 | `sales/magento_rma/store_name` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `sales/magento_rma/address` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 街道地址 | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 城市 | `sales/magento_rma/city` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 州/省 | `sales/magento_rma/region_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 邮政编码 | `sales/magento_rma/zip` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 国家/地区 | `sales/magento_rma/country_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将RMA电子邮件副本发送到 | `sales_email/magento_rma/copy_to` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将RMA授权电子邮件副本发送到 | `sales_email/magento_rma_auth/copy_to` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将RMA评论电子邮件副本发送到 | `sales_email/magento_rma_comment/copy_to` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将RMA评论电子邮件副本发送到 | `sales_email/magento_rma_customer_comment/copy_to` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Google API路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **Google API**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 帐号 | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## 高级类别

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **高级**.

### 管理员敏感路径和特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **高级** > **管理员**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 自定义管理员URL | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自定义管理路径 | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 系统敏感路径和系统特定路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **高级** > **系统**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 错误电子邮件收件人 | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问列表 | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 错误电子邮件发件人 | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 对开发人员敏感且特定于系统的路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **高级** > **开发人员**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 允许的IP（以逗号分隔） | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## 高级类别

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **高级**.

### 系统路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **高级** > **系统**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 主机 | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 端口(25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 后端主机 | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 后端端口 | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 开发人员路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **高级** > **开发人员**.

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 将JS错误记录到会话存储密钥 | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

## 支付敏感型和特定于系统的路径

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **销售** > **付款**.

### 常规变量

| 名称 | 配置路径 | 仅限商业？ | 加密？ |
|--------------|--------------|--------------|--------------|
| 商户国家 | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

>[!INFO]
>
>您对此变量的选择决定了 [国际路径](#international-paths) 您可以使用。

### PayPal敏感路径和特定于系统的路径

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 与PayPal商户帐户关联的电子邮件（可选） | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户帐户ID | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发布者ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密码 | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 登录 | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自定义端点主机名或IP地址 | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒模式 | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 调试模式 | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 调试模式 | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| SFTP凭据 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal Payflow Pro敏感和特定于系统的路径

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 用户 | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密码 | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 自定义路径 | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 用户 | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密码 | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 合作伙伴 | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理主机 | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理端口 | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 调试模式 | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| SFTP凭据 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 信用卡设置 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal Payflow Link敏感路径和特定于系统的路径

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 用户 | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密码 | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 使用代理 | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 代理主机 | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 代理端口 | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 调试模式 | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 取消URL和返回URL的URL方法 | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 调试模式 | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| SFTP凭据 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal Payments Pro敏感和特定于系统的路径

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API用户名 | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API密码 | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API签名 | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API证书 | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理主机 | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理端口 | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒模式 | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| SFTP凭据 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal Payments Pro托管敏感和特定于系统的路径

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 调试模式 | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| SFTP凭据 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Braintree敏感路径和特定于系统的路径

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 商户ID | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 公钥 | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 私钥 | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户帐户ID | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| Kount Merchant ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 覆盖商户名称 | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电话 | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### 检查/货币订单路径

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 将检查发送到 | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将检查发送到 | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### 国际路径

| 名称 | 配置路径 | 仅限商业？ | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 交易键 | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_au/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_au/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_au/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_au/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 付款响应密码 | `payment_au/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_au/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒模式 | `payment_au/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_au/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_au/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_au/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_au/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_au/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_au/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_es/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_es/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_es/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_es/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 付款响应密码 | `payment_es/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_es/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_es/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 调试 | `payment_es/worldpay/debug` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_es/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_es/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_es/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_es/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_es/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_es/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_es/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_nz/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 测试模式 | `payment_nz/worldpay/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_nz/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_nz/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_nz/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_nz/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_nz/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_nz/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_nz/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 代理主机 | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 代理端口 | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 调试模式 | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 取消URL和返回URL的URL方法 | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 测试模式 | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_us/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_us/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_us/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 测试模式 | `payment_us/worldpay/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_us/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_us/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_us/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_us/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_us/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_us/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_us/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 测试模式 | `payment_gb/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 测试模式 | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_gb/worldpay/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_gb/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_gb/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_gb/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_gb/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_gb/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_gb/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_gb/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_de/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_de/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_de/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_de/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 交易键 | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款响应密码 | `payment_de/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_de/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 调试 | `payment_de/worldpay/debug` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_de/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_de/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_de/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_de/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_de/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_de/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_de/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 网关URL | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 交易键 | `payment_other/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_other/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_other/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新订单状态 | `payment_other/cybersource/order_status` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 测试模式 | `payment_other/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 付款响应密码 | `payment_other/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_other/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_other/worldpay/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_other/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_other/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_other/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_other/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_other/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_other/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_other/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_ca/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_ca/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_ca/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新订单状态 | `payment_ca/cybersource/order_status` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 测试模式 | `payment_ca/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 付款响应密码 | `payment_ca/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 远程管理员授权密码 | `payment_ca/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_ca/worldpay/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_ca/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_ca/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_ca/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_ca/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_ca/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_ca/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_ca/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_hk/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_hk/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_hk/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_hk/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款响应密码 | `payment_hk/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_hk/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_hk/worldpay/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密钥 | `payment_hk/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_hk/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_hk/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_hk/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_hk/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_hk/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_jp/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_jp/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_jp/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新订单状态 | `payment_jp/cybersource/order_status` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 测试模式 | `payment_jp/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 付款响应密码 | `payment_jp/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_jp/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_jp/worldpay/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_jp/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_jp/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_jp/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_jp/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_jp/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_jp/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_jp/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_fr/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_fr/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_fr/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_fr/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 付款响应密码 | `payment_fr/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_fr/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_fr/worldpay/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_fr/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_fr/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_fr/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_fr/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_fr/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_fr/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_fr/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 网关URL | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易详细信息URL | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_it/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_it/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_it/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_it/cybersource/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 付款响应密码 | `payment_it/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_it/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 测试模式 | `payment_it/worldpay/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 沙盒模式 | `payment_it/eway/sandbox_flag` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) |
| 实时API密钥 | `payment_it/eway/live_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时API密码 | `payment_it/eway/live_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 实时客户端加密密钥 | `payment_it/eway/live_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密钥 | `payment_it/eway/sandbox_api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒API密码 | `payment_it/eway/sandbox_api_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 沙盒客户端加密密钥 | `payment_it/eway/sandbox_encryption_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API密钥 | `fraud_protection/signifyd/api_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API URL | `fraud_protection/signifyd/api_url` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  | ![特定于系统](/help/assets/configuration/cloud-env.png) | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员安装ID | `payment_au/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_au/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将检查发送到 | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_es/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_es/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员安装ID | `payment_es/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 |
| SFTP凭据 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_nz/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_nz/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_nz/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_nz/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_nz/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安装ID | `payment_nz/worldpay/installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款响应密码 | `payment_nz/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员安装ID | `payment_nz/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_nz/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_nz/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_us/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_us/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_us/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安装ID | `payment_us/worldpay/installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款响应密码 | `payment_us/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员安装ID | `payment_us/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_us/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_us/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将检查发送到 | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_gb/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_gb/cybersource/transaction_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_gb/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 访问密钥 | `payment_gb/cybersource/access_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 密钥 | `payment_gb/cybersource/secret_key` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易键 | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安装ID | `payment_gb/worldpay/installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 付款响应密码 | `payment_gb/worldpay/response_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员安装ID | `payment_gb/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员授权密码 | `payment_gb/worldpay/auth_password` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票给 | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将检查发送到 | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_de/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_de/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安装ID | `payment_de/worldpay/installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 远程管理员安装ID | `payment_de/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_de/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票给 | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将检查发送到 | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新订单状态 | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_other/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_other/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安装ID | `payment_other/worldpay/installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员安装ID | `payment_other/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_other/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票给 | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将检查发送到 | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 新订单状态 | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_ca/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_ca/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安装ID | `payment_ca/worldpay/installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员安装ID | `payment_ca/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_ca/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票给 | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将检查发送到 | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_hk/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_hk/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安装ID | `payment_hk/worldpay/installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员安装ID | `payment_hk/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_hk/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 签名字段 | `payment_hk/worldpay/signature_fields` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票给 | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将检查发送到 | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_jp/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_jp/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安装ID | `payment_jp/worldpay/installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 远程管理员安装ID | `payment_jp/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_jp/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 签名字段 | `payment_jp/worldpay/signature_fields` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票给 | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将检查发送到 | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_fr/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_fr/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安装ID | `payment_fr/worldpay/installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员安装ID | `payment_fr/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_fr/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 签名字段 | `payment_fr/worldpay/signature_fields` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| SFTP凭据 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 支付支票给 | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将检查发送到 | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| API登录ID | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 电子邮件客户 | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商家电子邮件 | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 商户ID | `payment_it/cybersource/merchant_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 配置文件ID | `payment_it/cybersource/profile_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) | ![加密](/help/assets/configuration/cloud-enc.png) |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 安装ID | `payment_it/worldpay/installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 远程管理员安装ID | `payment_it/worldpay/admin_installation_id` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 交易的MD5密钥 | `payment_it/worldpay/md5_secret` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}
