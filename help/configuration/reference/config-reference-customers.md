---
title: 客户配置路径参考
description: 请参阅客户配置值列表。
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# 客户配置路径参考

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **客户**.

的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 将这些值写入共享配置文件， `app/etc/config.php`，它应位于源代码管理中。 要选择覆盖任何配置设置或设置敏感设置，请参阅 [使用环境变量覆盖配置设置](override-config-settings.md#environment-variables). 本主题包含 _not_ 列表 [敏感值和系统特定值](config-reference-sens.md).

## 新闻稿路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **客户** > **新闻稿**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 允许来宾订阅 | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要确认 | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 确认电子邮件发件人 | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 确认电子邮件模板 | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功电子邮件发件人 | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功电子邮件模板 | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 退订电子邮件发件人 | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 退订电子邮件模板 | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 客户配置路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **客户** > **客户配置**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 联机分钟间隔 | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 共享客户帐户 | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用对客户组的自动分配 | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计税依据 | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认组 | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效增值税标识的组 — 国内 | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效增值税ID的组 — 合内 | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 无效增值税ID的组 | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 验证错误组 | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在每次交易时验证 | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 禁用基于增值税ID的自动组更改的默认值 | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在店面上显示增值税编号 | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认欢迎电子邮件 | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 默认的无密码欢迎电子邮件 | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 电子邮件发件人 | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 要求确认电子邮件 | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 确认链接电子邮件 | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 欢迎电子邮件 | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生成人性化的客户ID | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密码重置保护类型 | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大密码重置请求数 | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密码重置请求之间的最短时间 | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 忘记电子邮件模板 | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 提醒电子邮件模板 | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重置密码模板 | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 密码模板电子邮件发件人 | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 恢复链接过期时间（小时） | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在登录/忘记密码表单时启用自动完成 | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 所需字符类的数量 | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 锁定帐户的最大登录失败数 | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小密码长度 | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 锁定时间（分钟） | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 街道地址中的行数 | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示前缀 | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 前缀下拉选项 | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示中间名（初始） | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示后缀 | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 后缀下拉选项 | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示出生日期 | `customer/address/dob_show`<br>与当前的安全和隐私最佳实践保持一致，在收集或处理此类数据之前，请确保您了解与存储客户完整出生日期（月、日、年）以及其他个人标识符（如全名）相关的任何潜在法律和安全风险。 | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示税/增值税号 | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示性别 | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用存储点数功能 | `customer/magento_customerbalance/is_enabled` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 向客户显示商店信用历史记录 | `customer/magento_customerbalance/show_history` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 退款商店贷项自动 | `customer/magento_customerbalance/refund_automatically` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 存储信用更新电子邮件发件人 | `customer/magento_customerbalance/email_identity` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 存储信用更新电子邮件模板 | `customer/magento_customerbalance/email_template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 登录后将客户重定向到帐户功能板 | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 文本 | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 文本一行 | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用客户区段功能 | `customer/magento_customersegment/is_enabled` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 在店面上启用CAPTCHA | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 字体 | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示模式 | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 尝试登录失败的次数 | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 验证码超时（分钟） | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 符号数 | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 验证码中使用的符号 | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 区分大小写 | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 希望列表路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **客户** > **愿望列表**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 已启用 | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用多个愿望列表 | `wishlist/general/multiple_enabled` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 多个愿望列表的数量 | `wishlist/general/multiple_wishlist_number` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 电子邮件发件人 | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 电子邮件模板 | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许发送的最大电子邮件数 | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 电子邮件文本长度限制 | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示愿望列表摘要 | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 邀请路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **客户** > **邀请**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 启用邀请功能 | `magento_invitation/general/enabled` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 在店面上启用邀请 | `magento_invitation/general/enabled_on_front` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 引荐客户组 | `magento_invitation/general/registration_use_inviter_group` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 新帐户注册 | `magento_invitation/general/registration_required_invitation` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 允许客户向邀请电子邮件添加自定义消息 | `magento_invitation/general/allow_customer_message` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 允许一次发送的最大邀请数 | `magento_invitation/general/max_invitation_amount_per_send` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 客户邀请电子邮件发件人 | `magento_invitation/email/identity` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 客户邀请电子邮件模板 | `magento_invitation/email/template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## 奖励点路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **客户** > **奖励积分**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 启用奖励点数功能 | `magento_reward/general/is_enabled` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 在店面上启用奖励点功能 | `magento_reward/general/is_enabled_on_front` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 客户可能会看到奖励积分历史记录 | `magento_reward/general/publish_history` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 奖励积分余额赎回阈值 | `magento_reward/general/min_points_balance` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 奖金上限积分余额 | `magento_reward/general/max_points_balance` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 奖励积分过期时间（天） | `magento_reward/general/expiration_days` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 奖励积分到期计算 | `magento_reward/general/expiry_calculation` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 自动退款奖励积分 | `magento_reward/general/refund_automatically` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 自动从退款金额中扣除奖励积分 | `magento_reward/general/deduct_automatically` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 登陆页面 | `magento_reward/general/landing_page` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 购买 | `magento_reward/points/order` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 注册 | `magento_reward/points/register` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 新闻稿注册 | `magento_reward/points/newsletter` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 将邀请转换为客户 | `magento_reward/points/invitation_customer` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 邀请客户转化数量限制 | `magento_reward/points/invitation_customer_limit` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 将邀请转换为订单 | `magento_reward/points/invitation_order` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 订单转化邀请数量限制 | `magento_reward/points/invitation_order_limit` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 将邀请转换为订单奖励 | `magento_reward/points/invitation_order_frequency` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 审核提交 | `magento_reward/points/review` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 奖励审查提交数量限制 | `magento_reward/points/review_limit` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 电子邮件发件人 | `magento_reward/notification/email_sender` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 默认订阅客户 | `magento_reward/notification/subscribe_by_default` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 余额更新电子邮件 | `magento_reward/notification/balance_update_template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 奖励点到期警告电子邮件 | `magento_reward/notification/expiry_warning_template` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 之前（天）到期警告 | `magento_reward/notification/expiry_day_before` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## 促销活动路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **客户** > **促销活动**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 启用提醒电子邮件 | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 频率 | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 间隔 | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小时分钟数 | `promo/magento_reminder/minutes` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 开始时间 | `promo/magento_reminder/time` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 每次运行的最大电子邮件数 | `promo/magento_reminder/limit` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 电子邮件发送失败阈值 | `promo/magento_reminder/threshold` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 提醒电子邮件发件人 | `promo/magento_reminder/identity` | ![仅限商务](/help/assets/configuration/cloud-ee.png) |
| 代码长度 | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代码格式 | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代码前缀 | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 代码后缀 | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将每X个字符划线 | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 礼品注册路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **客户** > **礼品登记**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 启用礼品注册表 | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注册者数 | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 电子邮件模板 | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 电子邮件发件人 | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 电子邮件模板 | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 电子邮件发件人 | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大已发送电子邮件阈值 | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 电子邮件模板 | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 电子邮件发件人 | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 永久性购物车路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **客户** > **永久性购物车**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 启用持久性 | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 持久性生命周期（秒） | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用“记住我” | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| “记住我”默认值 | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注销时清除持久性 | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persist Shopping Cart | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 持久愿望列表 | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留最近订购的项目 | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留当前比较的产品 | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persist Comparison History | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留最近查看的产品 | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留客户群组成员资格和分段 | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
