---
title: ACSD-55610：部分取消的订单的折扣金额不正确
description: 应用ACSD-55610补丁以修复部分取消的订单折扣金额不正确的Adobe Commerce问题。
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: b7b94c9d-e027-4601-837b-d70b7ff8bd2c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%
---
# ACSD-55610：部分取消的订单的折扣金额不正确

ACSD-55610修补程序修复了部分取消的订单的折扣金额不正确的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.43时，此修补程序可用。 修补程序ID为ACSD-55610。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

部分取消的订单的折扣金额不正确。

<u>重现步骤</u>：

1. 创建购物车价格规则。

   * *[!UICONTROL Rule Name]*： *冬季促销*
   * *[!UICONTROL Active]* = *是*
   * *[!UICONTROL Websites]* = *主网站*
   * 选择所有客户组。
   * 选择特定优惠券。
   * *[!UICONTROL Coupon Code]*： *WINTER10*
   * *[!UICONTROL Conditions]*： *[!UICONTROL If ALL of these conditions are TRUE]*： *小计(不包括 税)等于或大于75*
   * 应用&#x200B;*[!UICONTROL Percent of product price discount]*。
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*： *是*

1. 创建三个价格设置为100的产品。
1. 将三个产品添加到购物车。
1. 申请优惠券。
1. 下订单。
1. 为订单中的一个项目开票并装运它。
1. 取消其他两个项目。
1. 检查`base_discount_canceled`列。

<u>预期的结果</u>：

`base_discount_cancelled`中的折扣金额正确反映。

<u>实际结果</u>：

`base_discount_cancelled`不正确。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
