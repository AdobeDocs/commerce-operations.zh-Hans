---
title: 客户个人信息参考（版本1.x）
description: 了解Magento1.x中客户个人信息的数据流和数据库实体映射。
exl-id: 8b01418d-8ca1-48fc-9577-a324ed3109d1
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# 客户个人信息参考（版本1.x）

>[!NOTE]
>
>这是一系列主题中的一个，旨在帮助Adobe Commerce商家和开发人员为遵守隐私法规做好准备。 请咨询您的法律顾问，确定您的企业是否以及如何应遵守任何法律义务。

在开发隐私法规的合规性程序时，请参考以下数据流图和数据库实体映射，例如：

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## 数据流图

数据流图显示了客户和管理员可以在店面和管理员上输入和检索的数据类型。

### 前端数据入口点

用户在注册帐户、结帐期间以及类似事件时，可以输入客户、地址和付款信息。

![前端数据入口点](../../assets/security-compliance/frontend-data-entry-points.svg)

### 前端数据访问点

客户登录并查看多个不同的页面或结帐时，Commerce会加载客户信息。

![前端数据访问点](../../assets/security-compliance/frontend-data-access-points.svg)

### 后端数据入口点

商家可以从管理员输入客户、地址和付款信息，以创建客户或订单。

![后端数据入口点](../../assets/security-compliance/backend-data-entry-points.svg)

### 后端数据访问点

当商家查看多种类型的网格、单击网格查看详细信息和执行各种其他任务时，Commerce会加载客户信息。

![后端数据访问点](../../assets/security-compliance/backend-data-access-points.svg)

## 数据库实体

Magento1将客户信息存储在customer 、 sales和其他数据库表中。

### 客户数据

Magento1将客户信息存储在`customer_entity`和`customer_address_entity`表中。 这两个表都有多个引用表，它们可以包含自定义客户属性。

#### `customer_entity`和引用表

`customer_entity`表中的以下列包含客户信息：

| 列 | 数据类型 |
| --- | --- |
| `email` | varchar(255) |

这些表引用`customer_entity`，并且可以包含自定义客户属性：

| 表 | 列 | 数据类型 |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | 日期时间 |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | 文本 |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity`和引用表

以下表引用`customer_address_entity`，并且可以包含自定义客户属性：

| 表 | 列 | 数据类型 |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | 日期时间 |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | 文本 |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 订单数据

`sales_flat_order`和相关表包含客户名称、帐单和送货地址及相关信息。

#### `sales_flat_order`表

`sales_order`表中的以下列包含客户信息：

| 列 | 数据类型 |
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

#### `sales_flat_order_address`表

`sales_flat_order_address`表包含客户的地址。

| 列 | 数据类型 |
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
| `vat_id` | 文本 |

#### `sales_flat_order_grid`表

`sales_flat_order_grid`表中的以下列包含客户信息：

| 列 | 数据类型 |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### `sales_flat_order_payment`表

`sales_flat_order_payment`表中的以下列包含客户信息：

| 列 | 数据类型 |
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

### 报价数据

引号包含客户的姓名、电子邮件、地址和相关信息。

#### `sales_flat_quote`表

`sales_flat_quote`表中的以下列包含客户信息：

| 列 | 数据类型 |
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
| `customer_dob` | 日期时间 |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `sales_flat_quote_address`表

`sales_flat_quote_address`表中的以下列包含客户信息：

| 列 | 数据类型 |
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

#### `sales_flat_quote_payment`表

`sales_flat_quote_payment`表包括信用卡信息和其他事务信息。

| 列 | 数据类型 |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | smallint(5) |
| `cc_exp_year` | smallint(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | smallint(5) |
| `cc_ss_start_year` | smallint(5) |

### 存档数据

以下表和列包含客户信息：

| 表 | 列 | 数据类型 |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `customer_id` | int(10) |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar(255) |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar(255) |

### 销售数据

以下表和列包含客户信息：

| 表 | 列 | 数据类型 |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### RMA数据

以下RMA表和列包含客户信息：

| 表 | 列 | 数据类型 |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar(255) |
| `enterprise_rma_grid` | `customer_id` | int(10) |
| `enterprise_rma_grid` | `customer_name` | varchar(255) |

### 其他数据

以下表和列包含客户信息：

| 表 | 列 | 数据类型 |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar(128) |
| `core_email_queue_recipients` | `recipient_name` | varchar(255) |
| `customer_flowpassword` | `email` | varchar(255) |
| `customer_flowpassword` | `ip` | varchar(50) |
| `enterprise_giftregistry_person` | `email` | varchar(150) |
| `enterprise_giftregistry_person` | `firstname` | varchar(100) |
| `enterprise_giftregistry_person` | `lastname` | varchar(100) |
| `enterprise_giftregistry_person` | `middlename` | 文本 |
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
| `persistent_session` | `info` | 文本 |
| `poll_vote` | `customer_id` | int(10) |
| `poll_vote` | `ip_address` | varbinary(16) |
| `rating_option_vote` | `customer_id` | int(10) |
| `rating_option_vote` | `remote_ip` | varchar(50) |
| `rating_option_vote` | `remote_ip_long` | varbinary(516) |
| `send_friend_log` | `ip` | varbinary(16) |

引用客户的其他表：

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
