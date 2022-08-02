---
title: B2B扩展配置路径参考
description: 请参阅与B2B相关的配置值列表。
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---


# B2B扩展配置路径参考

_这适用于安装了B2B for Adobe Commerce的实例。_

本主题列出了Commerce Enterprise B2B扩展的配置路径。 的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 将这些值写入共享配置文件， `app/etc/config.php`，它应位于源代码管理中。

>[!INFO]
>
>此参考列表 _仅_ 用于Adobe Commerce的B2B特有配置路径。 此扩展包含Adobe Commerce的所有配置路径。

有关这些配置路径，请参阅：

- [付款配置路径](config-reference-payment.md)
- [敏感和特定于系统的配置路径引用](config-reference-sens.md)

要选择覆盖任何配置设置或设置敏感设置，请参阅 [使用环境变量覆盖配置设置](override-config-settings.md#environment-variables).

## 一般类别

此部分列出了可用于管理员下方选项的变量名称和配置路径 **[!UICONTROL Stores]** >设置> **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### B2B功能路径

这些配置值在的“管理员”中可用 **[!UICONTROL Stores]** >设置> **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| 名称 | 配置路径 | 加密？ | 特定于系统？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 启用公司 | `btob/website_configuration/company_active` |  |  |  |
| 启用共享目录 | `btob/website_configuration/sharedcatalog_active` |  |  |  |
| 启用B2B报价 | `btob/website_configuration/negotiablequote_active` |  |  |  |
| 启用快速订单 | `btob/website_configuration/quickorder_active` |  |  |  |
| 启用申请列表 | `btob/website_configuration/requisition_list_active` |  |  |  |
| 适用的付款方法 | `btob/default_b2b_payment_methods/applicable_payment_methods` |  |  |  |
| 付款方法 | `btob/default_b2b_payment_methods/available_payment_methods` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## 客户类别

此部分列出了可用于管理员下方选项的变量名称和配置路径 **[!UICONTROL Stores]** >设置> **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### 公司配置路径

这些配置值在的“管理员”中可用 **[!UICONTROL Stores]** >设置> **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| 名称 | 配置路径 | 加密？ | 特定于系统？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|
| 允许从店面注册公司 | `company/general/allow_company_registration` |  |  |  |
| 公司注册电子邮件收件人 | `company/email/company_registration` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将公司注册电子邮件副本发送到 | `company/email/company_registration_copy` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发送电子邮件复制方法 | `company/email/company_copy_method` |  |  |  |
| 默认公司注册电子邮件 | `company/email/company_notify_admin_template` |  |  |  |
| 与客户相关的电子邮件 | `company/email/heading_customer` |  |  |  |
| 默认销售代表分配的电子邮件 | `company/email/customer_sales_representative_template` |  |  |  |
| 将公司默认分配给客户电子邮件 | `company/email/customer_company_customer_assign_template` |  |  |  |
| 默认分配公司管理员电子邮件 | `company/email/customer_assign_super_user_template` |  |  |  |
| 默认公司管理员不活动电子邮件 | `company/email/customer_inactivate_super_user_template` |  |  |  |
| 默认公司管理员已更改为成员电子邮件 | `company/email/customer_remove_super_user_template` |  |  |  |
| 默认客户状态活动电子邮件 | `company/email/customer_account_activated_template` |  |  |  |
| 默认客户状态不活动电子邮件 | `company/email/customer_account_locked_template` |  |  |  |
| 公司状态更改 | `company/email/heading_company_status` |  |  |  |
| 公司状态更改电子邮件收件人 | `company/email/company_status_change` |  |  |  |
| 将公司状态更改电子邮件副本发送到 | `company/email/company_status_change_copy` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发送电子邮件复制方法 | `company/email/company_status_copy_method` |  |  |  |
| 默认公司状态更改为活动1封电子邮件 | `company/email/company_status_pending_approval_to_active_template` |  |  |  |
| 默认公司状态更改为活动2封电子邮件 | `company/email/company_status_rejected_blocked_to_active_template` |  |  |  |
| 默认公司状态更改为已拒绝的电子邮件 | `company/email/company_status_rejected_template` |  |  |  |
| 默认公司状态更改为已阻止的电子邮件 | `company/email/company_status_blocked_template` |  |  |  |
| 默认公司状态更改为待批准电子邮件 | `company/email/company_status_pending_approval_template` |  |  |  |
| 公司信用 | `company/email/heading_company_credit` |  |  |  |
| 公司信用更改电子邮件发件人 | `company/email/company_credit_change` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 将公司信用更改电子邮件副本发送到 | `company/email/company_credit_change_copy` |  |  |  |
| 发送电子邮件复制方法 | `company/email/company_credit_copy_method` |  |  |  |
| 已分配的电子邮件模板 | `company/email/credit_allocated_email_template` |  |  |  |
| 更新了电子邮件模板 | `company/email/credit_updated_email_template` |  |  |  |
| 报销电子邮件模板 | `company/email/credit_reimbursed_email_template` |  |  |  |
| 退回的电子邮件模板 | `company/email/credit_refunded_email_template` |  |  |  |
| 还原的电子邮件模板 | `company/email/credit_reverted_email_template` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### 申请列出路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **客户** > **申请列表**.

| 名称 | 配置路径 | 加密？ | 特定于系统？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 申请列表数 | `requisitionlist/general/number_requisition_lists` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## 销售类别

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **销售**.

### 销售电子邮件路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **销售电子邮件**.

| 名称 | 配置路径 | 加密？ | 特定于系统？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 已启用 | `sales_email/quote/enabled` |  |  |  |
| 更新了报价模板（对买方） | `sales_email/quote/updated_buyer_template` |  |  |  |
| 拒绝报价模板（对买方） | `sales_email/quote/declined_buyer_template` |  |  |  |
| 新报价模板（对卖方） | `sales_email/quote/new_seller_template` |  |  |  |
| 更新了报价模板（对卖方） | `sales_email/quote/updated_seller_template` |  |  |  |
| 报价到期（48小时后） | `sales_email/quote/expire_two_days_template` |  |  |  |
| 报价到期（24小时后） | `sales_email/quote/expire_one_day_template` |  |  |  |
| 重置过期日期 | `sales_email/quote/expire_reset_template` |  |  |  |
| 将报价电子邮件副本发送到 | `sales_email/quote/copy_to` |  |  | ![敏感](/help/assets/configuration/cloud-sens.png) |
| 发送报价电子邮件复制方法 | `sales_email/quote/copy_method` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### 引号路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **报价**.

| 名称 | 配置路径 | 加密？ | 特定于系统？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 最小金额 | `quote/general/minimum_amount` |  |  |  |
| 最小金额消息 | `quote/general/minimum_amount_message` |  |  |  |
| 默认过期时间 | `quote/general/default_expiration_period` |  |  |  |
| 上传的文件格式 | `quote/attached_files/file_formats` |  |  |  |
| 最大文件大小 | `quote/attached_files/maximum_file_size` |  |  |  |
| 最小金额 | `quote/general/minimum_amount` |  |  |  |
| 最小金额消息 | `quote/general/minimum_amount_message` |  |  |  |
| 默认过期时间 | `quote/general/default_expiration_period` |  |  |  |
| 上传的文件格式 | `quote/attached_files/file_formats` |  |  |  |
| 最大文件大小 | `quote/attached_files/maximum_file_size` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## 付款方法路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **销售** > **付款方法**.

>[!INFO]
>
>可用路径取决于您选择的商家国家/地区。

| 名称 | 配置路径 | 加密？ | 特定于系统？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 已启用 | `payment/au/companycredit/active` |  |  |  |
| 标题 | `payment/au/companycredit/title` |  |  |  |
| 新订单状态 | `payment/au/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/au/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/au/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/au/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/au/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/au/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/es/companycredit/active` |  |  |  |
| 标题 | `payment/es/companycredit/title` |  |  |  |
| 新订单状态 | `payment/es/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/es/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/es/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/es/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/es/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/es/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/companycredit/active` |  |  |  |
| 标题 | `payment/companycredit/title` |  |  |  |
| 新订单状态 | `payment/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/nz/companycredit/active` |  |  |  |
| 标题 | `payment/nz/companycredit/title` |  |  |  |
| 新订单状态 | `payment/nz/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/nz/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/nz/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/nz/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/nz/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/nz/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/us/companycredit/active` |  |  |  |
| 标题 | `payment/us/companycredit/title` |  |  |  |
| 新订单状态 | `payment/us/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/us/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/us/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/us/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/us/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/us/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/gb/companycredit/active` |  |  |  |
| 标题 | `payment/gb/companycredit/title` |  |  |  |
| 新订单状态 | `payment/gb/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/gb/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/gb/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/gb/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/gb/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/gb/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/de/companycredit/active` |  |  |  |
| 标题 | `payment/de/companycredit/title` |  |  |  |
| 新订单状态 | `payment/de/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/de/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/de/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/de/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/de/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/de/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/other/companycredit/active` |  |  |  |
| 标题 | `payment/other/companycredit/title` |  |  |  |
| 新订单状态 | `payment/other/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/other/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/other/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/other/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/other/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/other/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/ca/companycredit/active` |  |  |  |
| 标题 | `payment/ca/companycredit/title` |  |  |  |
| 新订单状态 | `payment/ca/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/ca/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/ca/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/ca/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/ca/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/ca/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/hk/companycredit/active` |  |  |  |
| 标题 | `payment/hk/companycredit/title` |  |  |  |
| 新订单状态 | `payment/hk/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/hk/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/hk/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/hk/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/hk/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/hk/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/jp/companycredit/active` |  |  |  |
| 标题 | `payment/jp/companycredit/title` |  |  |  |
| 新订单状态 | `payment/jp/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/jp/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/jp/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/jp/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/jp/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/jp/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/fr/companycredit/active` |  |  |  |
| 标题 | `payment/fr/companycredit/title` |  |  |  |
| 新订单状态 | `payment/fr/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/fr/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/fr/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/fr/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/fr/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/fr/companycredit/sort_order` |  |  |  |
| 已启用 | `payment/it/companycredit/active` |  |  |  |
| 标题 | `payment/it/companycredit/title` |  |  |  |
| 新订单状态 | `payment/it/companycredit/order_status` |  |  |  |
| 从适用国家/地区付款 | `payment/it/companycredit/allowspecific` |  |  |  |
| 特定国家/地区的付款 | `payment/it/companycredit/specificcountry` |  |  |  |
| 最低订单总计 | `payment/it/companycredit/min_order_total` |  |  |  |
| 最大订单总计 | `payment/it/companycredit/max_order_total` |  |  |  |
| 排序顺序 | `payment/it/companycredit/sort_order` |  |  |  |

{style=&quot;table-layout:auto&quot;}
