---
title: 支付配置路径参考
description: 了解Adobe Commerce Admin中的付款配置路径和方法值。 了解PayPal、信用卡和支付网关配置选项。
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '4113'
ht-degree: 0%

---

# 支付配置路径参考

这些配置值在&#x200B;**商店** >设置> **配置** > **销售** > **付款方式**&#x200B;的管理员中可用。

[`magento app:config:dump`命令](../cli/export-configuration.md)将这些值写入到共享配置文件`app/etc/config.php`中，该文件应位于源代码控制中。 若要选择性地覆盖任何配置设置或设置敏感设置，请参阅[使用环境变量覆盖配置设置](override-config-settings.md#environment-variables)。 此主题&#x200B;_不_&#x200B;列出[敏感且特定于系统的值](config-reference-sens.md)。

这些设置按支付方式进一步组织。

## PayPal路径

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| 启用此解决方案 | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用In-Context签出体验 | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用PayPal点数 | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用PayPal点数 | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示 | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示 | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示 | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 显示 | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大小 | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在产品详细信息页面上显示 | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在购物车上显示 | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款适用自 | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 适用国家/地区付款自 | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用SSL验证 | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转移购物车行项目 | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 跳过订单审核步骤 | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转移购物车行项目 | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转移配送选项 | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 快捷方式按钮风格 | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用PayPal来宾签出 | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要客户的帐单地址 | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 帐单协议注册 | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款适用自 | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 适用国家/地区付款自 | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用SSL验证 | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 转移购物车行项目 | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在帐单协议向导中允许 | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用自动提取 | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划 | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 时间 | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal产品标志 | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 页面样式 | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题图像URL | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题背景颜色 | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题边框颜色 | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 页面背景颜色 | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用此解决方案 | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序PayPal点数 | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在产品详细信息页面上显示 | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 授权兑现期（天） | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 订单有效期（天） | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 子项授权的数量 | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在购物车上显示 | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款适用自 | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 适用国家/地区付款自 | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用SSL验证 | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payments Pro

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| API身份验证方法 | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| API使用代理 | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Payments Pro托管解决方案（英国）

这些选项仅在您选择英国作为[商家国家/地区](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths)时才可用。

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| 启用此解决方案 | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在“付款信息”步骤中显示“快速结帐” | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款适用自 | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 适用国家/地区付款自 | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用SSL验证 | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow Pro

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| 保险库已启用 | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保险库标题 | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许的信用卡类型 | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款适用自 | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 适用国家/地区付款自 | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用SSL验证 | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要CVV条目 | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒绝事务处理，如果： | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS街不匹配 | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS Zip不匹配 | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 国际AVS指示符不匹配 | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 卡安全代码不匹配 | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 供应商 | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用代理 | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 合作伙伴 | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 供应商 | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用代理 | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用此解决方案 | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款适用自 | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 适用国家/地区付款自 | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用SSL验证 | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV条目可编辑 | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要CVV条目 | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送电子邮件确认 | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow链接

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| 合作伙伴 | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 供应商 | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用工资流链接 | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用Express签出 | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序PayPal点数 | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款适用自 | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 适用国家/地区付款自 | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用SSL验证 | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV条目可编辑 | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 需要CVV条目 | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送电子邮件确认 | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 零小计签出路径

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| 已启用 | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 货到付款路径

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| 已启用 | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 银行转帐支付路径

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| 已启用 | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 支票或汇票路径

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| 已启用 | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将支票支付给 | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 采购订单路径

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| 已启用 | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 国际路径

>[!INFO]
>
>可用的路径由您选择的[商家国家/地区](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths)决定。

| 名称 | 配置路径 | 仅限Commerce？ | 是否加密？ |
|--------------|--------------|--------------|--------------|
| SFTP凭据 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用此解决方案 | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡设置 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒绝事务处理，如果： | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将支票支付给 | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送支票到 | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_nz/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_nz/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_nz/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 新订单状态 | `payment_nz/cybersource/order_status` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_nz/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_nz/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_nz/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_nz/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_nz/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_nz/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_nz/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_nz/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_nz/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_nz/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_nz/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 签名字段 | `payment_nz/worldpay/signature_fields` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_nz/worldpay/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_nz/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_nz/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_nz/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_nz/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_nz/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_nz/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_nz/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_nz/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_nz/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_nz/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_nz/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_nz/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_nz/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_nz/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_nz/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_nz/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_hk/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_hk/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_hk/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 新订单状态 | `payment_hk/cybersource/order_status` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_hk/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_hk/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_hk/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_hk/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_hk/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_hk/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_hk/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_hk/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_hk/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_hk/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_hk/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_hk/worldpay/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_hk/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_hk/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_hk/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_hk/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_hk/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_hk/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_hk/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_hk/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_hk/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_hk/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 沙盒模式 | `payment_hk/eway/sandbox_flag` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_hk/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_hk/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_hk/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_hk/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_hk/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_hk/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将支票支付给 | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_es/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_es/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_es/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 配置文件ID | `payment_es/cybersource/profile_id` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |
| 新订单状态 | `payment_es/cybersource/order_status` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_es/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_es/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_es/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_es/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_es/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_es/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_es/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_es/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_es/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 安装Id | `payment_es/worldpay/installation_id` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 远程管理员安装ID | `payment_es/worldpay/admin_installation_id` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_es/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_es/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 签名字段 | `payment_es/worldpay/signature_fields` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试模式 | `payment_es/worldpay/sandbox_flag` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_es/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_es/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_es/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_es/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_es/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_es/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_es/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_es/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_es/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_es/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_es/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_es/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_es/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_es/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_es/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_es/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_it/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_it/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_it/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 新订单状态 | `payment_it/cybersource/order_status` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_it/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_it/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_it/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_it/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_it/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_it/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_it/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_it/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_it/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_it/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_it/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 签名字段 | `payment_it/worldpay/signature_fields` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_it/worldpay/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_it/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_it/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_it/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_it/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_it/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_it/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_it/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_it/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_it/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_it/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_it/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_it/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_it/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_it/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_it/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_it/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_fr/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_fr/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_fr/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 新订单状态 | `payment_fr/cybersource/order_status` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_fr/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_fr/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_fr/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_fr/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_fr/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_fr/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_fr/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_fr/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_fr/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_fr/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_fr/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_fr/worldpay/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_fr/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_fr/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_fr/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_fr/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_fr/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_fr/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_fr/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_fr/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_fr/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_fr/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_fr/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_fr/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_fr/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_fr/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_fr/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_fr/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_jp/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_jp/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_jp/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_jp/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_jp/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_jp/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_jp/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_jp/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_jp/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_jp/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_jp/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_jp/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_jp/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_jp/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_jp/worldpay/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_jp/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_jp/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_jp/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_jp/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_jp/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_jp/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_jp/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_jp/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_jp/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_jp/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_jp/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_jp/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_jp/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_jp/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_jp/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_jp/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡设置 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒绝事务处理，如果： | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将支票支付给 | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 发送支票到 | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_au/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_au/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_au/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 商家ID | `payment_au/cybersource/merchant_id` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |
| 配置文件ID | `payment_au/cybersource/profile_id` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) | ![已加密](/help/assets/configuration/cloud-enc.png) |
| 新订单状态 | `payment_au/cybersource/order_status` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_au/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_au/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_au/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_au/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_au/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_au/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_au/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_au/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_au/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 安装Id | `payment_au/worldpay/installation_id` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_au/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_au/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 签名字段 | `payment_au/worldpay/signature_fields` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_au/worldpay/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试模式 | `payment_au/worldpay/sandbox_flag` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_au/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_au/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_au/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_au/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_au/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_au/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_au/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_au/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_au/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_au/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_au/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_au/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_au/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_au/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_au/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_au/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用此解决方案 | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡设置 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒绝事务处理，如果： | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡设置 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒绝事务处理，如果： | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_ca/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_ca/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_ca/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_ca/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_ca/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_ca/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_ca/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_ca/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_ca/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_ca/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_ca/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_ca/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_ca/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_ca/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 签名字段 | `payment_ca/worldpay/signature_fields` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_ca/worldpay/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_ca/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_ca/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_ca/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_ca/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_ca/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_ca/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_ca/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_ca/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_ca/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_ca/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_ca/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_ca/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_ca/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_ca/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_ca/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_ca/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 向客户发送电子邮件 | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_other/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_other/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_other/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_other/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_other/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_other/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_other/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_other/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_other/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_other/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_other/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_other/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_other/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_other/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 签名字段 | `payment_other/worldpay/signature_fields` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_other/worldpay/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_other/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_other/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_other/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_other/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_other/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_other/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_other/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_other/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_other/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_other/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_other/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_other/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_other/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_other/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_other/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_other/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_de/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_de/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_de/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 新订单状态 | `payment_de/cybersource/order_status` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_de/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_de/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_de/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_de/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_de/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_de/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_de/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_de/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_de/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_de/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_de/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 签名字段 | `payment_de/worldpay/signature_fields` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试模式 | `payment_de/worldpay/sandbox_flag` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_de/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_de/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_de/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_de/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_de/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_de/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_de/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_de/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_de/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_de/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_de/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_de/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_de/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_de/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_de/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_de/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将支票支付给 | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_gb/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_gb/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_gb/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 新订单状态 | `payment_gb/cybersource/order_status` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_gb/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_gb/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_gb/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_gb/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_gb/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_gb/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_gb/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_gb/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_gb/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 交易的MD5密码 | `payment_gb/worldpay/md5_secret` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_gb/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_gb/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 签名字段 | `payment_gb/worldpay/signature_fields` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_gb/worldpay/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_gb/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_gb/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_gb/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_gb/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_gb/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_gb/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_gb/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_gb/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_gb/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_gb/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_gb/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_gb/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_gb/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_gb/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_gb/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_gb/eway/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 计划提取 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡设置 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒绝事务处理，如果： | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 启用PayPal点数 | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡设置 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 拒绝事务处理，如果： | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 计划提取 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal商家页面样式 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自动为所有项目开票 | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 说明 | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 将支票支付给 | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 付款操作 | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 标题 | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新订单状态 | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接受的货币 | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 调试 | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡类型 | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 信用卡验证 | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自适用国家/地区的付款 | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 来自特定国家/地区的付款 | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小订单总计 | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大订单总计 | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 排序顺序 | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 已启用 | `payment_us/cybersource/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_us/cybersource/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_us/cybersource/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 新订单状态 | `payment_us/cybersource/order_status` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_us/cybersource/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_us/cybersource/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_us/cybersource/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_us/cybersource/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最小订单总计 | `payment_us/cybersource/min_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 最大订单总计 | `payment_us/cybersource/max_order_total` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_us/cybersource/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_us/worldpay/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_us/worldpay/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 允许编辑联系人信息 | `payment_us/worldpay/fix_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 隐藏联系人信息 | `payment_us/worldpay/hide_contact` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 签名字段 | `payment_us/worldpay/signature_fields` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_us/worldpay/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 测试的付款操作 | `payment_us/worldpay/test_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_us/worldpay/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家的付款 | `payment_us/worldpay/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_us/worldpay/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为CVV疑似欺诈 | `payment_us/worldpay/cvv_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_us/worldpay/avs_fraud_case` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_us/worldpay/sort_order` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 已启用 | `payment_us/eway/active` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 连接类型 | `payment_us/eway/connection_type` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 标题 | `payment_us/eway/title` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 付款操作 | `payment_us/eway/payment_action` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 调试 | `payment_us/eway/debug` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 信用卡类型 | `payment_us/eway/cctypes` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自适用国家/地区的付款 | `payment_us/eway/allowspecific` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 来自特定国家/地区的付款 | `payment_us/eway/specificcountry` | ![仅限Commerce](/help/assets/configuration/cloud-ee.png) |
| 排序顺序 | `payment_us/eway/sort_order` | |

{style="table-layout:auto"}
