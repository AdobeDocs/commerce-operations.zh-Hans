---
title: 客户个人信息参考（版本2.x）
description: 了解Adobe Commerce和Magento Open Source2.x中客户个人信息的数据流图和数据库实体映射。
source-git-commit: 2120e5bb912a89c58611ef9e23661a54e40a14f1
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---


# 客户个人信息参考（版本2.x）

>[!NOTE]
>
>这是帮助Adobe Commerce和Magento Open Source商家和开发人员为遵守隐私法规做准备的一系列主题中的一个主题。 请咨询您的法律顾问，以确定您的企业是否以及如何遵守任何法律义务。

在开发隐私法规合规性程序时，请参考以下数据流图和数据库实体映射，例如：

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## 数据流图

数据流图显示了客户和管理员可以输入和从店面和管理员检索的数据类型。

### 前端数据入口点

用户在注册帐户、结帐期间和类似事件时可以输入客户、地址和付款信息。

![前端数据入口点](../../assets/security-compliance/frontend-data-entry-points.svg)

### 前端数据接入点

Adobe Commerce和Magento Open Source在客户登录并查看多个不同页面或签出时加载客户信息。

![前端数据接入点](../../assets/security-compliance/frontend-data-access-points.svg)

### 后端数据输入点

商户在从管理员创建客户或订单时，可以输入客户信息、地址数据和付款数据。

![后端数据输入点](../../assets/security-compliance/backend-data-entry-points.svg)

### 后端数据访问点

Adobe Commerce和Magento Open Source在商户查看多种类型的网格时加载客户信息，单击网格以查看详细信息，并执行各种其他任务。

![后端数据访问点](../../assets/security-compliance/backend-data-access-points.svg)

## 数据库实体

Adobe Commerce和Magento Open Source主要在客户、地址、订单、报价和付款表中存储特定于客户的信息。 其他表包含对客户ID的引用。

### 客户数据

Adobe Commerce和Magento Open Source可配置为存储以下客户属性：

- 出生日期
- 电子邮件
- 名字
- 性别
- 姓氏
- 中间名/初始名
- 名称前缀
- 名称后缀

>[!NOTE]
>
>与当前的安全和隐私最佳实践保持一致，在收集或处理此类数据之前，请确保您了解与存储客户完整出生日期（月、日、年）以及其他个人标识符（如全名）相关的任何潜在法律和安全风险。

#### `customer_entity` 和“customer_entity”引用

中的以下列 `customer_entity` 表包含客户信息：

| 列 | 数据类型 |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | 日期 |
| `gender` | smallint(5) |

这些表引用 `customer_entity` 和可以包含自定义客户属性：

| 表 | 列 | 数据类型 |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | date |
| `customer_entity_decimal` | `value` | 小数(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | 文本 |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` 表

中的以下列 `customer_grid_flat` 表包含客户信息：

| 列 | 数据类型 |
| -------------------- | ------------ |
| `name` | 文本 |
| `email` | varchar(255) |
| `dob` | 日期 |
| `gender` | int(11) |
| `shipping_full` | 文本 |
| `billing_full` | 文本 |
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

### 地址数据

Adobe Commerce和Magento Open Source存储以下客户属性：

- 城市
- 公司
- 国家/地区
- 传真
- 名字
- 姓氏
- 中间名/初始名
- 名称前缀
- 名称后缀
- 电话号码
- 州/省
- 省/自治区ID
- 街道地址
- 增值税号
- 邮政编码

#### `customer_address_entity` 和 `customer_address_entity` 引用

中的以下列 `customer_address_entity` 表包含客户信息：

| 列 | 数据类型 |
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
| `street` | 文本 |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

这些表引用 `customer_address_entity` 和可以包含自定义客户属性：

| 表 | 列 | 数据类型 |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | date |
| `customer_address_entity_decimal` | `value` | 小数(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | 文本 |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 订单数据

的 `sales_order` 和相关表包含客户名称、帐单和送货地址以及相关数据。

#### `sales_order` 表

中的以下列 `sales_order` 表包含客户信息：

| 列 | 数据类型 |
| --------------------- | ------------ |
| `customer_dob` | date |
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

#### `sales_order_address` 表

的 `sales_order_address` 表包含客户的地址。

| 列 | 数据类型 |
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

#### `sales_order_grid` 表

中的以下列 `sales_order_grid` 表包含客户信息：

| 列 | 数据类型 |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### 报价数据

报价包含客户的名称、电子邮件、地址和相关信息。

#### `quote` 表

中的以下列 `quote` 表包含客户信息：

| 列 | 数据类型 |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | date |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address` 表

中的以下列 `quote_address` 表包含客户信息：

| 列 | 数据类型 |
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

### 付款数据

的 `sales_order_payment` 表包括信用卡信息和其他交易信息。

| 列 | 数据类型 |
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
| `additional_information` | 文本 |

### 邀请数据

可以配置Adobe Commerce和Magento Open Source，以便客户能够向私人销售和活动发送邀请。

#### `magento_invitation` 表

的 `magento_invitation` 表包含客户ID、电子邮件和反向链接ID。

| 列 | 数据类型 |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` 表

的 `magento_invitation_track` 表格还包含客户信息。

| 列 | 数据类型 |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### 引用客户的其他表

下表包含 `customer_id` 列：

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
