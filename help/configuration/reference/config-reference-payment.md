---
title: 支付配置路径参考
description: 了解Adobe Commerce Admin中的付款配置路径和方法值。 了解PayPal、信用卡和支付网关配置选项。
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '5833'
ht-degree: 0%

---

# 支付配置路径参考

这些配置值在&#x200B;**商店** >设置> **配置** > **销售** > **付款方式**&#x200B;的管理员中可用。

[`magento app:config:dump`命令](../cli/export-configuration.md)将这些值写入到共享配置文件`app/etc/config.php`中，该文件应位于源代码控制中。 若要选择性地覆盖任何配置设置或设置敏感设置，请参阅[使用环境变量覆盖配置设置](override-config-settings.md#environment-variables)。 此主题执行&#x200B;_全部_&#x200B;列出[敏感和系统特定的值](config-reference-sens.md)。

这些设置按支付方式进一步组织。

## PayPal路径

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| 启用此解决方案 | `payment/payflowpro/active` | 全部 |
| 启用In-Context签出体验 | `payment/paypal_express/in_context` | 全部 |
| 启用PayPal点数 | `payment/payflow_express_bml/active` | 全部 |
| 启用PayPal点数 | `payment/paypal_express_bml/active` | 全部 |
| 显示 | `payment/paypal_express_bml/homepage_display` | 全部 |
| 位置 | `payment/paypal_express_bml/homepage_position` | 全部 |
| 大小 | `payment/paypal_express_bml/homepage_size` | 全部 |
| 显示 | `payment/paypal_express_bml/categorypage_display` | 全部 |
| 位置 | `payment/paypal_express_bml/categorypage_position` | 全部 |
| 大小 | `payment/paypal_express_bml/categorypage_size` | 全部 |
| 显示 | `payment/paypal_express_bml/productpage_display` | 全部 |
| 位置 | `payment/paypal_express_bml/productpage_position` | 全部 |
| 大小 | `payment/paypal_express_bml/productpage_size` | 全部 |
| 显示 | `payment/paypal_express_bml/checkout_display` | 全部 |
| 位置 | `payment/paypal_express_bml/checkout_position` | 全部 |
| 大小 | `payment/paypal_express_bml/checkout_size` | 全部 |
| 在产品详细信息页面上显示 | `payment/payflow_express/visible_on_product` | 全部 |
| 在购物车上显示 | `payment/payflow_express/visible_on_cart` | 全部 |
| 付款适用自 | `payment/payflow_express/allowspecific` | 全部 |
| 适用国家/地区付款自 | `payment/payflow_express/specificcountry` | 全部 |
| 启用SSL验证 | `payment/payflow_express/verify_peer` | 全部 |
| 转移购物车行项目 | `payment/payflow_express/line_items_enabled` | 全部 |
| 跳过订单审核步骤 | `payment/paypal_express/skip_order_review_step` | 全部 |
| 转移购物车行项目 | `payment/paypal_express/line_items_enabled` | 全部 |
| 转移配送选项 | `payment/paypal_express/transfer_shipping_options` | 全部 |
| 快捷方式按钮风格 | `paypal/wpp/button_flavor` | 全部 |
| 启用PayPal来宾签出 | `payment/paypal_express/solution_type` | 全部 |
| 需要客户的帐单地址 | `payment/paypal_express/require_billing_address` | 全部 |
| 帐单协议注册 | `payment/paypal_express/allow_ba_signup` | 全部 |
| 已启用 | `payment/paypal_billing_agreement/active` | 全部 |
| 标题 | `payment/paypal_billing_agreement/title` | 全部 |
| 排序顺序 | `payment/paypal_billing_agreement/sort_order` | 全部 |
| 付款操作 | `payment/paypal_billing_agreement/payment_action` | 全部 |
| 付款适用自 | `payment/paypal_billing_agreement/allowspecific` | 全部 |
| 适用国家/地区付款自 | `payment/paypal_billing_agreement/specificcountry` | 全部 |
| 启用SSL验证 | `payment/paypal_billing_agreement/verify_peer` | 全部 |
| 转移购物车行项目 | `payment/paypal_billing_agreement/line_items_enabled` | 全部 |
| 在帐单协议向导中允许 | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | 全部 |
| 启用自动提取 | `paypal/fetch_reports/active` | 全部 |
| 计划 | `paypal/fetch_reports/schedule` | 全部 |
| 时间 | `paypal/fetch_reports/time` | 全部 |
| PayPal产品标志 | `paypal/style/logo` | 全部 |
| 页面样式 | `paypal/style/page_style` | 全部 |
| 标题图像URL | `paypal/style/paypal_hdrimg` | 全部 |
| 标题背景颜色 | `paypal/style/paypal_hdrbackcolor` | 全部 |
| 标题边框颜色 | `paypal/style/paypal_hdrbordercolor` | 全部 |
| 页面背景颜色 | `paypal/style/paypal_payflowcolor` | 全部 |
| 启用此解决方案 | `payment/paypal_express/active` | 全部 |
| 排序顺序PayPal点数 | `payment/paypal_express_bml/sort_order` | 全部 |
| 标题 | `payment/paypal_express/title` | 全部 |
| 排序顺序 | `payment/paypal_express/sort_order` | 全部 |
| 付款操作 | `payment/paypal_express/payment_action` | 全部 |
| 在产品详细信息页面上显示 | `payment/paypal_express/visible_on_product` | 全部 |
| 授权总期限（天） | `payment/paypal_express/authorization_hoAllr_period` | 全部 |
| 订单有效期（天） | `payment/paypal_express/order_valid_period` | 全部 |
| 子项授权的数量 | `payment/paypal_express/child_authorization_number` | 全部 |
| 在购物车上显示 | `payment/paypal_express/visible_on_cart` | 全部 |
| 子项授权的数量 | `payment/paypal_express/child_authorization_number` | 全部 |
| 付款适用自 | `payment/paypal_express/allowspecific` | 全部 |
| 子项授权的数量 | `payment/paypal_express/child_authorization_number` | 全部 |
| 适用国家/地区付款自 | `payment/paypal_express/specificcountry` | 全部 |
| 子项授权的数量 | `payment/paypal_express/child_authorization_number` | 全部 |
| 启用SSL验证 | `payment/paypal_express/verify_peer` | 全部 |
| 子项授权的数量 | `payment/paypal_express/child_authorization_number` | 全部 |
| 计划提取 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |

{style="table-layout:auto"}

## PayPal Payments Pro

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| API身份验证方法 | `paypal/wpp/api_authentication` | 全部 |
| API使用代理 | `paypal/wpp/use_proxy` | 全部 |
| 计划提取 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | 全部 |
| 计划提取 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | 全部 |

{style="table-layout:auto"}

## Payments Pro托管解决方案（英国）

这些选项仅在您选择英国作为[商家国家/地区](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths)时才可用。

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| 启用此解决方案 | `payment/hosted_pro/active` | 全部 |
| 标题 | `payment/hosted_pro/title` | 全部 |
| 排序顺序 | `payment/hosted_pro/sort_order` | 全部 |
| 付款操作 | `payment/hosted_pro/payment_action` | 全部 |
| 在“付款信息”步骤中显示“快速结帐” | `payment/hosted_pro/display_ec` | 全部 |
| 付款适用自 | `payment/hosted_pro/allowspecific` | 全部 |
| 适用国家/地区付款自 | `payment/hosted_pro/specificcountry` | 全部 |
| 启用SSL验证 | `payment/hosted_pro/verify_peer` | 全部 |

{style="table-layout:auto"}

## PayPal Payflow Pro

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| 保险库已启用 | `payment/payflowpro_cc_vault/active` | 全部 |
| 标题 | `payment/payflowpro/title` | 全部 |
| 保险库标题 | `payment/payflowpro_cc_vault/title` | 全部 |
| 排序顺序 | `payment/payflowpro/sort_order` | 全部 |
| 付款操作 | `payment/payflowpro/payment_action` | 全部 |
| 允许的信用卡类型 | `payment/payflowpro/cctypes` | 全部 |
| 付款适用自 | `payment/payflowpro/allowspecific` | 全部 |
| 适用国家/地区付款自 | `payment/payflowpro/specificcountry` | 全部 |
| 启用SSL验证 | `payment/payflowpro/verify_peer` | 全部 |
| 需要CVV条目 | `payment/payflowpro/useccv` | 全部 |
| 拒绝事务处理，如果： | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | 全部 |
| AVS街不匹配 | `payment/payflowpro/avs_street` | 全部 |
| AVS Zip不匹配 | `payment/payflowpro/avs_zip` | 全部 |
| 国际AVS指示符不匹配 | `payment/payflowpro/avs_international` | 全部 |
| 卡安全代码不匹配 | `payment/payflowpro/avs_security_code` | 全部 |
| 供应商 | `payment/payflowpro/vendor` | 全部 |
| 使用代理 | `payment/payflowpro/use_proxy` | 全部 |
| 标题 | `payment/payflow_express/title` | 全部 |
| 排序顺序 | `payment/payflow_express/sort_order` | 全部 |
| 付款操作 | `payment/payflow_express/payment_action` | 全部 |
| 计划提取 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | 全部 |
| 合作伙伴 | `payment/payflow_advanced/partner` | 全部 |
| 供应商 | `payment/payflow_advanced/vendor` | 全部 |
| 使用代理 | `payment/payflow_advanced/use_proxy` | 全部 |
| 启用此解决方案 | `payment/payflow_advanced/active` | 全部 |
| 标题 | `payment/payflow_advanced/title` | 全部 |
| 排序顺序 | `payment/payflow_advanced/sort_order` | 全部 |
| 付款操作 | `payment/payflow_advanced/payment_action` | 全部 |
| 付款适用自 | `payment/payflow_advanced/allowspecific` | 全部 |
| 适用国家/地区付款自 | `payment/payflow_advanced/specificcountry` | 全部 |
| 启用SSL验证 | `payment/payflow_advanced/verify_peer` | 全部 |
| CVV条目可编辑 | `payment/payflow_advanced/csc_editable` | 全部 |
| 需要CVV条目 | `payment/payflow_advanced/csc_required` | 全部 |
| 发送电子邮件确认 | `payment/payflow_advanced/email_confirmation` | 全部 |

{style="table-layout:auto"}

## PayPal Payflow链接

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| 合作伙伴 | `payment/payflow_link/partner` | 全部 |
| 供应商 | `payment/payflow_link/vendor` | 全部 |
| 启用工资流链接 | `payment/payflow_link/active` | 全部 |
| 启用Express签出 | `payment/payflow_express/active` | 全部 |
| 排序顺序PayPal点数 | `payment/payflow_express_bml/sort_order` | 全部 |
| 付款适用自 | `payment/payflow_link/allowspecific` | 全部 |
| 适用国家/地区付款自 | `payment/payflow_link/specificcountry` | 全部 |
| 启用SSL验证 | `payment/payflow_link/verify_peer` | 全部 |
| CVV条目可编辑 | `payment/payflow_link/csc_editable` | 全部 |
| 需要CVV条目 | `payment/payflow_link/csc_required` | 全部 |
| 发送电子邮件确认 | `payment/payflow_link/email_confirmation` | 全部 |
| 计划提取 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | 全部 |
| 标题 | `payment/payflow_link/title` | 全部 |
| 排序顺序 | `payment/payflow_link/sort_order` | 全部 |
| 付款操作 | `payment/payflow_link/payment_action` | 全部 |

{style="table-layout:auto"}

## 零小计签出路径

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| 已启用 | `payment/free/active` | 全部 |
| 标题 | `payment/free/title` | 全部 |
| 新订单状态 | `payment/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment/free/specificcountry` | 全部 |
| 排序顺序 | `payment/free/sort_order` | 全部 |

{style="table-layout:auto"}

## 货到付款路径

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| 已启用 | `payment/cashondelivery/active` | 全部 |
| 标题 | `payment/cashondelivery/title` | 全部 |
| 新订单状态 | `payment/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment/cashondelivery/sort_order` | 全部 |

{style="table-layout:auto"}

## 银行转帐支付路径

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| 已启用 | `payment/banktransfer/active` | 全部 |
| 标题 | `payment/banktransfer/title` | 全部 |
| 新订单状态 | `payment/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment/banktransfer/specificcountry` | 全部 |
| 说明 | `payment/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment/banktransfer/sort_order` | 全部 |

{style="table-layout:auto"}

## 支票或汇票路径

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| 已启用 | `payment/checkmo/active` | 全部 |
| 标题 | `payment/checkmo/title` | 全部 |
| 新订单状态 | `payment/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment/checkmo/specificcountry` | 全部 |
| 将支票支付给 | `payment/checkmo/payable_to` | 全部 |
| 最小订单总计 | `payment/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment/checkmo/sort_order` | 全部 |

{style="table-layout:auto"}

## 采购订单路径

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| 已启用 | `payment/purchaseorder/active` | 全部 |
| 标题 | `payment/purchaseorder/title` | 全部 |
| 新订单状态 | `payment/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment/purchaseorder/sort_order` | 全部 |

{style="table-layout:auto"}

## 国际路径

>[!INFO]
>
>可用的路径由您选择的[商家国家/地区](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths)决定。

| 名称 | 配置路径 | Commerce版本支持？ |
|--------------|--------------|--------------|
| SFTP凭据 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | 全部 |
| 计划提取 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 启用此解决方案 | `payment/wps_express/active` | 全部 |
| 计划提取 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 信用卡设置 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | 全部 |
| 拒绝事务处理，如果： | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | 全部 |
| 计划提取 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | 全部 |
| 已启用 | `payment_nz/free/active` | 全部 |
| 标题 | `payment_nz/free/title` | 全部 |
| 新订单状态 | `payment_nz/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_nz/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_nz/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_nz/free/specificcountry` | 全部 |
| 排序顺序 | `payment_nz/free/sort_order` | 全部 |
| 已启用 | `payment_nz/cashondelivery/active` | 全部 |
| 标题 | `payment_nz/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_nz/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_nz/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_nz/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_nz/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_nz/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_nz/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_nz/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_nz/banktransfer/active` | 全部 |
| 标题 | `payment_nz/banktransfer/title` | 全部 |
| 新订单状态 | `payment_nz/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_nz/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_nz/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_nz/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_nz/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_nz/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_nz/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_nz/checkmo/active` | 全部 |
| 标题 | `payment_nz/checkmo/title` | 全部 |
| 新订单状态 | `payment_nz/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_nz/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_nz/checkmo/specificcountry` | 全部 |
| 将支票支付给 | `payment_nz/checkmo/payable_to` | 全部 |
| 发送支票到 | `payment_nz/checkmo/mailing_address` | 全部 |
| 最小订单总计 | `payment_nz/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_nz/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_nz/checkmo/sort_order` | 全部 |
| 已启用 | `payment_nz/purchaseorder/active` | 全部 |
| 标题 | `payment_nz/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_nz/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_nz/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_nz/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_nz/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_nz/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_nz/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_nz/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_nz/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_nz/authorizenet_directpost/title` | 全部 |
| 新订单状态 | `payment_nz/authorizenet_directpost/order_status` | 全部 |
| 接受的货币 | `payment_nz/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_nz/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_nz/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_nz/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_nz/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_nz/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_nz/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_nz/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_nz/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_nz/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_nz/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_nz/cybersource/title` | 仅限Commerce Enterprise |
| 新订单状态 | `payment_nz/cybersource/order_status` | 仅限Commerce Enterprise |
| 调试 | `payment_nz/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_nz/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_nz/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_nz/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_nz/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_nz/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_nz/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_nz/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_nz/worldpay/title` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_nz/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_nz/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 签名字段 | `payment_nz/worldpay/signature_fields` | 仅限Commerce Enterprise |
| 调试 | `payment_nz/worldpay/debug` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_nz/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_nz/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_nz/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_nz/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_nz/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_nz/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_nz/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_nz/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_nz/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_nz/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_nz/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_nz/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_nz/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_nz/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_nz/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_nz/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | 全部 |
| 计划提取 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 已启用 | `payment_hk/free/active` | 全部 |
| 标题 | `payment_hk/free/title` | 全部 |
| 新订单状态 | `payment_hk/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_hk/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_hk/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_hk/free/specificcountry` | 全部 |
| 排序顺序 | `payment_hk/free/sort_order` | 全部 |
| 已启用 | `payment_hk/cashondelivery/active` | 全部 |
| 标题 | `payment_hk/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_hk/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_hk/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_hk/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_hk/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_hk/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_hk/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_hk/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_hk/banktransfer/active` | 全部 |
| 标题 | `payment_hk/banktransfer/title` | 全部 |
| 新订单状态 | `payment_hk/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_hk/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_hk/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_hk/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_hk/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_hk/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_hk/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_hk/checkmo/active` | 全部 |
| 标题 | `payment_hk/checkmo/title` | 全部 |
| 新订单状态 | `payment_hk/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_hk/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_hk/checkmo/specificcountry` | 全部 |
| 最小订单总计 | `payment_hk/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_hk/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_hk/checkmo/sort_order` | 全部 |
| 已启用 | `payment_hk/purchaseorder/active` | 全部 |
| 标题 | `payment_hk/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_hk/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_hk/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_hk/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_hk/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_hk/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_hk/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_hk/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_hk/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_hk/authorizenet_directpost/title` | 全部 |
| 新订单状态 | `payment_hk/authorizenet_directpost/order_status` | 全部 |
| 接受的货币 | `payment_hk/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_hk/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_hk/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_hk/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_hk/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_hk/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_hk/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_hk/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_hk/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_hk/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_hk/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_hk/cybersource/title` | 仅限Commerce Enterprise |
| 新订单状态 | `payment_hk/cybersource/order_status` | 仅限Commerce Enterprise |
| 调试 | `payment_hk/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_hk/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_hk/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_hk/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_hk/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_hk/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_hk/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_hk/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_hk/worldpay/title` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_hk/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_hk/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 调试 | `payment_hk/worldpay/debug` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_hk/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_hk/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_hk/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_hk/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_hk/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_hk/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_hk/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_hk/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_hk/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_hk/eway/title` | 仅限Commerce Enterprise |
| 沙盒模式 | `payment_hk/eway/sandbox_flag` | 仅限Commerce Enterprise |
| 付款操作 | `payment_hk/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_hk/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_hk/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_hk/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_hk/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_hk/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | 全部 |
| 计划提取 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 已启用 | `payment_es/free/active` | 全部 |
| 标题 | `payment_es/free/title` | 全部 |
| 新订单状态 | `payment_es/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_es/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_es/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_es/free/specificcountry` | 全部 |
| 排序顺序 | `payment_es/free/sort_order` | 全部 |
| 已启用 | `payment_es/cashondelivery/active` | 全部 |
| 标题 | `payment_es/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_es/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_es/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_es/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_es/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_es/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_es/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_es/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_es/banktransfer/active` | 全部 |
| 标题 | `payment_es/banktransfer/title` | 全部 |
| 新订单状态 | `payment_es/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_es/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_es/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_es/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_es/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_es/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_es/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_es/checkmo/active` | 全部 |
| 标题 | `payment_es/checkmo/title` | 全部 |
| 新订单状态 | `payment_es/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_es/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_es/checkmo/specificcountry` | 全部 |
| 将支票支付给 | `payment_es/checkmo/payable_to` | 全部 |
| 最小订单总计 | `payment_es/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_es/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_es/checkmo/sort_order` | 全部 |
| 已启用 | `payment_es/purchaseorder/active` | 全部 |
| 标题 | `payment_es/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_es/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_es/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_es/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_es/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_es/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_es/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_es/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_es/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_es/authorizenet_directpost/title` | 全部 |
| 新订单状态 | `payment_es/authorizenet_directpost/order_status` | 全部 |
| 接受的货币 | `payment_es/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_es/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_es/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_es/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_es/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_es/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_es/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_es/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_es/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_es/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_es/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_es/cybersource/title` | 仅限Commerce Enterprise |
| 配置文件ID | `payment_es/cybersource/profile_id` | 仅限Commerce Enterprise\| ![已加密](/help/assets/configuration/cloud-enc.png) |
| 新订单状态 | `payment_es/cybersource/order_status` | 仅限Commerce Enterprise |
| 调试 | `payment_es/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_es/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_es/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_es/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_es/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_es/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_es/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_es/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_es/worldpay/title` | 仅限Commerce Enterprise |
| 安装Id | `payment_es/worldpay/installation_id` | 仅限Commerce Enterprise |
| 远程管理员安装ID | `payment_es/worldpay/admin_installation_id` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_es/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_es/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 签名字段 | `payment_es/worldpay/signature_fields` | 仅限Commerce Enterprise |
| 测试模式 | `payment_es/worldpay/sandbox_flag` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_es/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_es/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_es/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_es/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_es/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_es/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_es/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_es/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_es/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_es/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_es/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_es/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_es/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_es/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_es/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_es/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | 全部 |
| 计划提取 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 已启用 | `payment_it/free/active` | 全部 |
| 标题 | `payment_it/free/title` | 全部 |
| 新订单状态 | `payment_it/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_it/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_it/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_it/free/specificcountry` | 全部 |
| 排序顺序 | `payment_it/free/sort_order` | 全部 |
| 已启用 | `payment_it/cashondelivery/active` | 全部 |
| 标题 | `payment_it/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_it/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_it/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_it/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_it/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_it/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_it/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_it/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_it/banktransfer/active` | 全部 |
| 标题 | `payment_it/banktransfer/title` | 全部 |
| 新订单状态 | `payment_it/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_it/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_it/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_it/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_it/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_it/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_it/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_it/checkmo/active` | 全部 |
| 标题 | `payment_it/checkmo/title` | 全部 |
| 新订单状态 | `payment_it/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_it/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_it/checkmo/specificcountry` | 全部 |
| 最小订单总计 | `payment_it/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_it/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_it/checkmo/sort_order` | 全部 |
| 已启用 | `payment_it/purchaseorder/active` | 全部 |
| 标题 | `payment_it/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_it/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_it/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_it/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_it/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_it/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_it/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_it/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_it/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_it/authorizenet_directpost/title` | 全部 |
| 新订单状态 | `payment_it/authorizenet_directpost/order_status` | 全部 |
| 接受的货币 | `payment_it/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_it/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_it/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_it/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_it/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_it/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_it/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_it/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_it/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_it/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_it/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_it/cybersource/title` | 仅限Commerce Enterprise |
| 新订单状态 | `payment_it/cybersource/order_status` | 仅限Commerce Enterprise |
| 调试 | `payment_it/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_it/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_it/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_it/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_it/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_it/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_it/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_it/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_it/worldpay/title` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_it/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_it/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 签名字段 | `payment_it/worldpay/signature_fields` | 仅限Commerce Enterprise |
| 调试 | `payment_it/worldpay/debug` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_it/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_it/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_it/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_it/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_it/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_it/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_it/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_it/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_it/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_it/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_it/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_it/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_it/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_it/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_it/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_it/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | 全部 |
| 计划提取 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 已启用 | `payment_fr/free/active` | 全部 |
| 标题 | `payment_fr/free/title` | 全部 |
| 新订单状态 | `payment_fr/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_fr/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_fr/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_fr/free/specificcountry` | 全部 |
| 排序顺序 | `payment_fr/free/sort_order` | 全部 |
| 已启用 | `payment_fr/cashondelivery/active` | 全部 |
| 标题 | `payment_fr/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_fr/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_fr/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_fr/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_fr/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_fr/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_fr/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_fr/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_fr/banktransfer/active` | 全部 |
| 标题 | `payment_fr/banktransfer/title` | 全部 |
| 新订单状态 | `payment_fr/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_fr/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_fr/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_fr/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_fr/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_fr/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_fr/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_fr/checkmo/active` | 全部 |
| 标题 | `payment_fr/checkmo/title` | 全部 |
| 新订单状态 | `payment_fr/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_fr/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_fr/checkmo/specificcountry` | 全部 |
| 最小订单总计 | `payment_fr/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_fr/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_fr/checkmo/sort_order` | 全部 |
| 已启用 | `payment_fr/purchaseorder/active` | 全部 |
| 标题 | `payment_fr/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_fr/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_fr/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_fr/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_fr/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_fr/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_fr/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_fr/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_fr/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_fr/authorizenet_directpost/title` | 全部 |
| 新订单状态 | `payment_fr/authorizenet_directpost/order_status` | 全部 |
| 接受的货币 | `payment_fr/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_fr/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_fr/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_fr/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_fr/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_fr/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_fr/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_fr/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_fr/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_fr/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_fr/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_fr/cybersource/title` | 仅限Commerce Enterprise |
| 新订单状态 | `payment_fr/cybersource/order_status` | 仅限Commerce Enterprise |
| 调试 | `payment_fr/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_fr/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_fr/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_fr/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_fr/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_fr/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_fr/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_fr/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_fr/worldpay/title` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_fr/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_fr/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 调试 | `payment_fr/worldpay/debug` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_fr/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_fr/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_fr/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_fr/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_fr/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_fr/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_fr/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_fr/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_fr/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_fr/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_fr/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_fr/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_fr/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_fr/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_fr/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_fr/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | 全部 |
| 计划提取 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 已启用 | `payment_jp/free/active` | 全部 |
| 标题 | `payment_jp/free/title` | 全部 |
| 新订单状态 | `payment_jp/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_jp/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_jp/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_jp/free/specificcountry` | 全部 |
| 排序顺序 | `payment_jp/free/sort_order` | 全部 |
| 已启用 | `payment_jp/cashondelivery/active` | 全部 |
| 标题 | `payment_jp/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_jp/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_jp/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_jp/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_jp/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_jp/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_jp/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_jp/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_jp/banktransfer/active` | 全部 |
| 标题 | `payment_jp/banktransfer/title` | 全部 |
| 新订单状态 | `payment_jp/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_jp/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_jp/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_jp/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_jp/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_jp/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_jp/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_jp/checkmo/active` | 全部 |
| 标题 | `payment_jp/checkmo/title` | 全部 |
| 新订单状态 | `payment_jp/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_jp/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_jp/checkmo/specificcountry` | 全部 |
| 最小订单总计 | `payment_jp/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_jp/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_jp/checkmo/sort_order` | 全部 |
| 已启用 | `payment_jp/purchaseorder/active` | 全部 |
| 标题 | `payment_jp/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_jp/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_jp/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_jp/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_jp/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_jp/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_jp/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_jp/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_jp/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_jp/authorizenet_directpost/title` | 全部 |
| 新订单状态 | `payment_jp/authorizenet_directpost/order_status` | 全部 |
| 接受的货币 | `payment_jp/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_jp/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_jp/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_jp/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_jp/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_jp/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_jp/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_jp/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_jp/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_jp/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_jp/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_jp/cybersource/title` | 仅限Commerce Enterprise |
| 调试 | `payment_jp/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_jp/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_jp/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_jp/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_jp/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_jp/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_jp/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_jp/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_jp/worldpay/title` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_jp/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_jp/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 调试 | `payment_jp/worldpay/debug` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_jp/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_jp/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_jp/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_jp/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_jp/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_jp/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_jp/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_jp/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_jp/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_jp/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_jp/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_jp/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_jp/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_jp/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_jp/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_jp/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | 全部 |
| 计划提取 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 信用卡设置 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | 全部 |
| 拒绝事务处理，如果： | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | 全部 |
| 计划提取 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | 全部 |
| 已启用 | `payment_au/free/active` | 全部 |
| 标题 | `payment_au/free/title` | 全部 |
| 新订单状态 | `payment_au/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_au/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_au/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_au/free/specificcountry` | 全部 |
| 排序顺序 | `payment_au/free/sort_order` | 全部 |
| 已启用 | `payment_au/cashondelivery/active` | 全部 |
| 标题 | `payment_au/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_au/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_au/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_au/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_au/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_au/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_au/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_au/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_au/banktransfer/active` | 全部 |
| 标题 | `payment_au/banktransfer/title` | 全部 |
| 新订单状态 | `payment_au/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_au/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_au/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_au/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_au/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_au/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_au/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_au/checkmo/active` | 全部 |
| 标题 | `payment_au/checkmo/title` | 全部 |
| 新订单状态 | `payment_au/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_au/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_au/checkmo/specificcountry` | 全部 |
| 将支票支付给 | `payment_au/checkmo/payable_to` | 全部 |
| 发送支票到 | `payment_au/checkmo/mailing_address` | 全部 |
| 最小订单总计 | `payment_au/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_au/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_au/checkmo/sort_order` | 全部 |
| 已启用 | `payment_au/purchaseorder/active` | 全部 |
| 标题 | `payment_au/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_au/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_au/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_au/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_au/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_au/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_au/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_au/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_au/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_au/authorizenet_directpost/title` | 全部 |
| 新订单状态 | `payment_au/authorizenet_directpost/order_status` | 全部 |
| 接受的货币 | `payment_au/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_au/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_au/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_au/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_au/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_au/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_au/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_au/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_au/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_au/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_au/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_au/cybersource/title` | 仅限Commerce Enterprise |
| 商家ID | `payment_au/cybersource/merchant_id` | 仅限Commerce Enterprise \| ![已加密](/help/assets/configuration/cloud-enc.png) |
| 配置文件ID | `payment_au/cybersource/profile_id` | 仅限Commerce Enterprise \| ![已加密](/help/assets/configuration/cloud-enc.png) |
| 新订单状态 | `payment_au/cybersource/order_status` | 仅限Commerce Enterprise |
| 调试 | `payment_au/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_au/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_au/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_au/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_au/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_au/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_au/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_au/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_au/worldpay/title` | 仅限Commerce Enterprise |
| 安装Id | `payment_au/worldpay/installation_id` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_au/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_au/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 签名字段 | `payment_au/worldpay/signature_fields` | 仅限Commerce Enterprise |
| 调试 | `payment_au/worldpay/debug` | 仅限Commerce Enterprise |
| 测试模式 | `payment_au/worldpay/sandbox_flag` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_au/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_au/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_au/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_au/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_au/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_au/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_au/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_au/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_au/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_au/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_au/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_au/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_au/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_au/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_au/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_au/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 启用此解决方案 | `payment/paypal_payment_pro/active` | 全部 |
| 信用卡设置 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | 全部 |
| 拒绝事务处理，如果： | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | 全部 |
| 计划提取 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | 全部 |
| 信用卡设置 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | 全部 |
| 拒绝事务处理，如果： | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | 全部 |
| 计划提取 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | 全部 |
| 计划提取 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | 全部 |
| 已启用 | `payment_ca/free/active` | 全部 |
| 标题 | `payment_ca/free/title` | 全部 |
| 新订单状态 | `payment_ca/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_ca/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_ca/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_ca/free/specificcountry` | 全部 |
| 排序顺序 | `payment_ca/free/sort_order` | 全部 |
| 已启用 | `payment_ca/cashondelivery/active` | 全部 |
| 标题 | `payment_ca/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_ca/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_ca/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_ca/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_ca/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_ca/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_ca/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_ca/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_ca/banktransfer/active` | 全部 |
| 标题 | `payment_ca/banktransfer/title` | 全部 |
| 新订单状态 | `payment_ca/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_ca/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_ca/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_ca/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_ca/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_ca/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_ca/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_ca/checkmo/active` | 全部 |
| 标题 | `payment_ca/checkmo/title` | 全部 |
| 新订单状态 | `payment_ca/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_ca/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_ca/checkmo/specificcountry` | 全部 |
| 最小订单总计 | `payment_ca/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_ca/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_ca/checkmo/sort_order` | 全部 |
| 已启用 | `payment_ca/purchaseorder/active` | 全部 |
| 标题 | `payment_ca/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_ca/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_ca/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_ca/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_ca/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_ca/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_ca/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_ca/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_ca/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_ca/authorizenet_directpost/title` | 全部 |
| 接受的货币 | `payment_ca/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_ca/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_ca/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_ca/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_ca/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_ca/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_ca/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_ca/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_ca/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_ca/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_ca/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_ca/cybersource/title` | 仅限Commerce Enterprise |
| 调试 | `payment_ca/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_ca/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_ca/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_ca/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_ca/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_ca/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_ca/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_ca/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_ca/worldpay/title` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_ca/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_ca/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 签名字段 | `payment_ca/worldpay/signature_fields` | 仅限Commerce Enterprise |
| 调试 | `payment_ca/worldpay/debug` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_ca/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_ca/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_ca/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_ca/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_ca/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_ca/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_ca/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_ca/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_ca/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_ca/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_ca/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_ca/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_ca/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_ca/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_ca/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_ca/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 已启用 | `payment_other/free/active` | 全部 |
| 标题 | `payment_other/free/title` | 全部 |
| 新订单状态 | `payment_other/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_other/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_other/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_other/free/specificcountry` | 全部 |
| 排序顺序 | `payment_other/free/sort_order` | 全部 |
| 已启用 | `payment_other/cashondelivery/active` | 全部 |
| 标题 | `payment_other/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_other/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_other/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_other/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_other/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_other/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_other/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_other/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_other/banktransfer/active` | 全部 |
| 标题 | `payment_other/banktransfer/title` | 全部 |
| 新订单状态 | `payment_other/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_other/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_other/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_other/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_other/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_other/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_other/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_other/checkmo/active` | 全部 |
| 标题 | `payment_other/checkmo/title` | 全部 |
| 新订单状态 | `payment_other/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_other/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_other/checkmo/specificcountry` | 全部 |
| 最小订单总计 | `payment_other/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_other/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_other/checkmo/sort_order` | 全部 |
| 已启用 | `payment_other/purchaseorder/active` | 全部 |
| 标题 | `payment_other/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_other/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_other/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_other/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_other/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_other/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_other/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_other/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_other/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_other/authorizenet_directpost/title` | 全部 |
| 接受的货币 | `payment_other/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_other/authorizenet_directpost/debug` | 全部 |
| 向客户发送电子邮件 | `payment_other/authorizenet_directpost/email_customer` | 全部 |
| 信用卡类型 | `payment_other/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_other/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_other/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_other/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_other/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_other/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_other/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_other/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_other/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_other/cybersource/title` | 仅限Commerce Enterprise |
| 调试 | `payment_other/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_other/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_other/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_other/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_other/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_other/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_other/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_other/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_other/worldpay/title` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_other/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_other/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 签名字段 | `payment_other/worldpay/signature_fields` | 仅限Commerce Enterprise |
| 调试 | `payment_other/worldpay/debug` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_other/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_other/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_other/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_other/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_other/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_other/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_other/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_other/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_other/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_other/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_other/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_other/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_other/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_other/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_other/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_other/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 已启用 | `payment_de/checkmo/active` | 全部 |
| 标题 | `payment_de/checkmo/title` | 全部 |
| 新订单状态 | `payment_de/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_de/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_de/checkmo/specificcountry` | 全部 |
| 最小订单总计 | `payment_de/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_de/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_de/checkmo/sort_order` | 全部 |
| 已启用 | `payment_de/banktransfer/active` | 全部 |
| 标题 | `payment_de/banktransfer/title` | 全部 |
| 新订单状态 | `payment_de/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_de/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_de/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_de/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_de/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_de/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_de/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_de/cashondelivery/active` | 全部 |
| 标题 | `payment_de/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_de/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_de/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_de/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_de/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_de/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_de/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_de/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_de/free/active` | 全部 |
| 标题 | `payment_de/free/title` | 全部 |
| 新订单状态 | `payment_de/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_de/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_de/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_de/free/specificcountry` | 全部 |
| 排序顺序 | `payment_de/free/sort_order` | 全部 |
| 已启用 | `payment_de/purchaseorder/active` | 全部 |
| 标题 | `payment_de/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_de/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_de/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_de/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_de/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_de/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_de/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_de/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_de/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_de/cybersource/title` | 仅限Commerce Enterprise |
| 新订单状态 | `payment_de/cybersource/order_status` | 仅限Commerce Enterprise |
| 调试 | `payment_de/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_de/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_de/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_de/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_de/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_de/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_de/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_de/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_de/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_de/authorizenet_directpost/title` | 全部 |
| 新订单状态 | `payment_de/authorizenet_directpost/order_status` | 全部 |
| 接受的货币 | `payment_de/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_de/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_de/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_de/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_de/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_de/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_de/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_de/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_de/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_de/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_de/worldpay/title` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_de/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_de/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 签名字段 | `payment_de/worldpay/signature_fields` | 仅限Commerce Enterprise |
| 测试模式 | `payment_de/worldpay/sandbox_flag` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_de/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_de/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_de/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_de/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_de/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_de/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_de/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_de/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_de/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_de/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_de/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_de/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_de/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_de/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_de/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_de/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 已启用 | `payment_gb/checkmo/active` | 全部 |
| 标题 | `payment_gb/checkmo/title` | 全部 |
| 新订单状态 | `payment_gb/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_gb/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_gb/checkmo/specificcountry` | 全部 |
| 将支票支付给 | `payment_gb/checkmo/payable_to` | 全部 |
| 最小订单总计 | `payment_gb/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_gb/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_gb/checkmo/sort_order` | 全部 |
| 已启用 | `payment_gb/banktransfer/active` | 全部 |
| 标题 | `payment_gb/banktransfer/title` | 全部 |
| 新订单状态 | `payment_gb/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_gb/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_gb/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_gb/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_gb/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_gb/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_gb/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_gb/cashondelivery/active` | 全部 |
| 标题 | `payment_gb/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_gb/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_gb/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_gb/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_gb/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_gb/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_gb/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_gb/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_gb/free/active` | 全部 |
| 标题 | `payment_gb/free/title` | 全部 |
| 新订单状态 | `payment_gb/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_gb/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_gb/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_gb/free/specificcountry` | 全部 |
| 排序顺序 | `payment_gb/free/sort_order` | 全部 |
| 已启用 | `payment_gb/purchaseorder/active` | 全部 |
| 标题 | `payment_gb/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_gb/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_gb/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_gb/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_gb/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_gb/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_gb/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_gb/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_gb/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_gb/cybersource/title` | 仅限Commerce Enterprise |
| 新订单状态 | `payment_gb/cybersource/order_status` | 仅限Commerce Enterprise |
| 调试 | `payment_gb/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_gb/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_gb/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_gb/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_gb/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_gb/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_gb/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_gb/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_gb/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_gb/authorizenet_directpost/title` | 全部 |
| 新订单状态 | `payment_gb/authorizenet_directpost/order_status` | 全部 |
| 接受的货币 | `payment_gb/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_gb/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_gb/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_gb/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_gb/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_gb/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_gb/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_gb/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_gb/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_gb/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_gb/worldpay/title` | 仅限Commerce Enterprise |
| 交易的MD5密码 | `payment_gb/worldpay/md5_secret` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_gb/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_gb/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 签名字段 | `payment_gb/worldpay/signature_fields` | 仅限Commerce Enterprise |
| 调试 | `payment_gb/worldpay/debug` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_gb/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_gb/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_gb/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_gb/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_gb/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_gb/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_gb/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_gb/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_gb/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_gb/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_gb/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_gb/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_gb/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_gb/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_gb/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_gb/eway/sort_order` | 仅限Commerce Enterprise |
| 计划提取 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | 全部 |
| 信用卡设置 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | 全部 |
| 拒绝事务处理，如果： | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | 全部 |
| 计划提取 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | 全部 |
| 启用PayPal点数 | `payment/wps_express_bml/active` | 全部 |
| 计划提取 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | 全部 |
| 信用卡设置 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | 全部 |
| 拒绝事务处理，如果： | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | 全部 |
| 计划提取 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | 全部 |
| 计划提取 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | 全部 |
| PayPal商家页面样式 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | 全部 |
| 已启用 | `payment_us/free/active` | 全部 |
| 标题 | `payment_us/free/title` | 全部 |
| 新订单状态 | `payment_us/free/order_status` | 全部 |
| 自动为所有项目开票 | `payment_us/free/payment_action` | 全部 |
| 来自适用国家/地区的付款 | `payment_us/free/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_us/free/specificcountry` | 全部 |
| 排序顺序 | `payment_us/free/sort_order` | 全部 |
| 已启用 | `payment_us/cashondelivery/active` | 全部 |
| 标题 | `payment_us/cashondelivery/title` | 全部 |
| 新订单状态 | `payment_us/cashondelivery/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_us/cashondelivery/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_us/cashondelivery/specificcountry` | 全部 |
| 说明 | `payment_us/cashondelivery/instructions` | 全部 |
| 最小订单总计 | `payment_us/cashondelivery/min_order_total` | 全部 |
| 最大订单总计 | `payment_us/cashondelivery/max_order_total` | 全部 |
| 排序顺序 | `payment_us/cashondelivery/sort_order` | 全部 |
| 已启用 | `payment_us/banktransfer/active` | 全部 |
| 标题 | `payment_us/banktransfer/title` | 全部 |
| 新订单状态 | `payment_us/banktransfer/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_us/banktransfer/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_us/banktransfer/specificcountry` | 全部 |
| 说明 | `payment_us/banktransfer/instructions` | 全部 |
| 最小订单总计 | `payment_us/banktransfer/min_order_total` | 全部 |
| 最大订单总计 | `payment_us/banktransfer/max_order_total` | 全部 |
| 排序顺序 | `payment_us/banktransfer/sort_order` | 全部 |
| 已启用 | `payment_us/checkmo/active` | 全部 |
| 标题 | `payment_us/checkmo/title` | 全部 |
| 新订单状态 | `payment_us/checkmo/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_us/checkmo/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_us/checkmo/specificcountry` | 全部 |
| 将支票支付给 | `payment_us/checkmo/payable_to` | 全部 |
| 最小订单总计 | `payment_us/checkmo/min_order_total` | 全部 |
| 最大订单总计 | `payment_us/checkmo/max_order_total` | 全部 |
| 排序顺序 | `payment_us/checkmo/sort_order` | 全部 |
| 已启用 | `payment_us/purchaseorder/active` | 全部 |
| 标题 | `payment_us/purchaseorder/title` | 全部 |
| 新订单状态 | `payment_us/purchaseorder/order_status` | 全部 |
| 来自适用国家/地区的付款 | `payment_us/purchaseorder/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_us/purchaseorder/specificcountry` | 全部 |
| 最小订单总计 | `payment_us/purchaseorder/min_order_total` | 全部 |
| 最大订单总计 | `payment_us/purchaseorder/max_order_total` | 全部 |
| 排序顺序 | `payment_us/purchaseorder/sort_order` | 全部 |
| 已启用 | `payment_us/authorizenet_directpost/active` | 全部 |
| 付款操作 | `payment_us/authorizenet_directpost/payment_action` | 全部 |
| 标题 | `payment_us/authorizenet_directpost/title` | 全部 |
| 新订单状态 | `payment_us/authorizenet_directpost/order_status` | 全部 |
| 接受的货币 | `payment_us/authorizenet_directpost/currency` | 全部 |
| 调试 | `payment_us/authorizenet_directpost/debug` | 全部 |
| 信用卡类型 | `payment_us/authorizenet_directpost/cctypes` | 全部 |
| 信用卡验证 | `payment_us/authorizenet_directpost/useccv` | 全部 |
| 来自适用国家/地区的付款 | `payment_us/authorizenet_directpost/allowspecific` | 全部 |
| 来自特定国家/地区的付款 | `payment_us/authorizenet_directpost/specificcountry` | 全部 |
| 最小订单总计 | `payment_us/authorizenet_directpost/min_order_total` | 全部 |
| 最大订单总计 | `payment_us/authorizenet_directpost/max_order_total` | 全部 |
| 排序顺序 | `payment_us/authorizenet_directpost/sort_order` | 全部 |
| 已启用 | `payment_us/cybersource/active` | 仅限Commerce Enterprise |
| 付款操作 | `payment_us/cybersource/payment_action` | 仅限Commerce Enterprise |
| 标题 | `payment_us/cybersource/title` | 仅限Commerce Enterprise |
| 新订单状态 | `payment_us/cybersource/order_status` | 仅限Commerce Enterprise |
| 调试 | `payment_us/cybersource/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_us/cybersource/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_us/cybersource/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_us/cybersource/specificcountry` | 仅限Commerce Enterprise |
| 最小订单总计 | `payment_us/cybersource/min_order_total` | 仅限Commerce Enterprise |
| 最大订单总计 | `payment_us/cybersource/max_order_total` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_us/cybersource/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_us/worldpay/active` | 仅限Commerce Enterprise |
| 标题 | `payment_us/worldpay/title` | 仅限Commerce Enterprise |
| 允许编辑联系人信息 | `payment_us/worldpay/fix_contact` | 仅限Commerce Enterprise |
| 隐藏联系人信息 | `payment_us/worldpay/hide_contact` | 仅限Commerce Enterprise |
| 签名字段 | `payment_us/worldpay/signature_fields` | 仅限Commerce Enterprise |
| 调试 | `payment_us/worldpay/debug` | 仅限Commerce Enterprise |
| 测试的付款操作 | `payment_us/worldpay/test_action` | 仅限Commerce Enterprise |
| 付款操作 | `payment_us/worldpay/payment_action` | 仅限Commerce Enterprise |
| 来自适用国家的付款 | `payment_us/worldpay/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_us/worldpay/specificcountry` | 仅限Commerce Enterprise |
| 将订单状态设置为CVV疑似欺诈 | `payment_us/worldpay/cvv_fraud_case` | 仅限Commerce Enterprise |
| 将订单状态设置为可疑的邮政编码AVS欺诈 | `payment_us/worldpay/avs_fraud_case` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_us/worldpay/sort_order` | 仅限Commerce Enterprise |
| 已启用 | `payment_us/eway/active` | 仅限Commerce Enterprise |
| 连接类型 | `payment_us/eway/connection_type` | 仅限Commerce Enterprise |
| 标题 | `payment_us/eway/title` | 仅限Commerce Enterprise |
| 付款操作 | `payment_us/eway/payment_action` | 仅限Commerce Enterprise |
| 调试 | `payment_us/eway/debug` | 仅限Commerce Enterprise |
| 信用卡类型 | `payment_us/eway/cctypes` | 仅限Commerce Enterprise |
| 来自适用国家/地区的付款 | `payment_us/eway/allowspecific` | 仅限Commerce Enterprise |
| 来自特定国家/地区的付款 | `payment_us/eway/specificcountry` | 仅限Commerce Enterprise |
| 排序顺序 | `payment_us/eway/sort_order` | |

{style="table-layout:auto"}
