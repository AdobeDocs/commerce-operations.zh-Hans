---
title: ACSD-47920：即使[!UICONTROL Allow Guest Checkout]关闭，访客用户也可以通过REST API下订单
description: 应用ACSD-47920修补程序以修复Adobe Commerce问题，该问题导致即使在[!UICONTROL Allow Guest Checkout]关闭的情况下，也可以通过REST API作为访客用户下达订单。
feature: REST, Checkout, Orders
role: Admin
exl-id: 27c74803-a3f3-46bc-9eb8-8e2c72c30cd9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%
---
# ACSD-47920：即使&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;关闭，访客用户也可以通过REST API下订单

ACSD-47920修补程序修复了以下问题：即使&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;处于关闭状态，也可以通过REST API以访客用户身份下达订单。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24时，此修补程序可用。 修补程序ID为ACSD-47920。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;已关闭，也可以通过Rest API以访客用户身份下达订单。

<u>重现步骤</u>：

1. 转到Adobe Commerce管理员> **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** >并将&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;设置为&#x200B;_否_。
1. 使用REST API将产品添加到购物车并下订单。

<u>预期的结果</u>：

如果&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;设置为&#x200B;_否_，则访客签出API返回错误&#x200B;*[!UICONTROL Sorry, guest checkout is not available]*。

<u>实际结果</u>：

访客签出API允许下达订单，即使&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;设置为&#x200B;_否_。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
