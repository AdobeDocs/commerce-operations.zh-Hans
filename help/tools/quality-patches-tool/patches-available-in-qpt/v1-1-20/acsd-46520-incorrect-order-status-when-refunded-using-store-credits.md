---
title: ACSD-46520：使用商店积分退款时订单状态不正确
description: 本文为使用商店积分退款时用户收到错误订单状态的问题提供了解决方案。
feature: Orders, Returns
role: Admin
exl-id: 67740003-a71e-41bf-afda-ca3e32290115
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%
---
# ACSD-46520：使用商店积分退款时订单状态不正确

ACSD-46520修补程序解决了使用商店积分退款时，用户得到的订单状态不正确的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.20时，此修补程序可用。 修补程序ID为ACSD-46520。 请注意，Adobe Commerce 2.4.5中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3和2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用商店积分退款时，用户会获得不正确的订单状态。

<u>重现步骤</u>：

1. 在店面创建客户帐户并登录。
1. 从管理员处将商店积分分配给客户。 店铺积分应覆盖整个订单。
1. 使用商店积分下订单。
1. 为订单开票。
1. 创建贷项通知单以退款订单的全部金额。
选中&#x200B;**[!UICONTROL Refund to store credit]**&#x200B;复选框。
1. 检查订单状态。

<u>预期的结果</u>：

订单状态为&#x200B;*已关闭*。

<u>实际结果</u>：

订单状态为&#x200B;*完成*，这不是正确的状态。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Quality Patches Tool指南中的[!DNL Magento Open Source]内部部署： [Quality Patches Tools > Usage](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
