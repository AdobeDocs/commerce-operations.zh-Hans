---
title: ACSD-65223：为B2B采购订单人工选择的条款和协议会导致错误
description: 应用ACSD-65223修补程序以修复Adobe Commerce问题，该问题导致在使用[!UICONTROL Purchase Orders]创建的订单无法通过在线支付方式（如信用卡）完成，因为结账需要条款和条件。
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 5a5d0774-3801-4688-86bd-58a390394cc0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-65223：为B2B采购订单人工选择的条款和协议会导致错误

ACSD-65223修补程序修复了以下问题：当需要结帐的条款和条件时，使用&#x200B;**[!UICONTROL Purchase Orders]**&#x200B;创建的订单无法通过信用卡等在线支付方式完成。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64时，此修补程序可用。 修补程序ID为ACSD-65223。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法）B2B 1.5.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）B2B 1.5.1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果下订单需要条款和条件，而您正尝试完成使用[!UICONTROL Purchase Orders]创建的订单，则无法使用信用卡等在线付款方式下订单。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]**，然后选择&#x200B;**[!UICONTROL B2B Features]**。
1. 将&#x200B;**[!UICONTROL Enable Company]**&#x200B;和&#x200B;**[!UICONTROL Enable Purchase Orders]**&#x200B;设置为&#x200B;*是*。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]**&#x200B;并创建新条件。 将&#x200B;**[!UICONTROL Applied]**&#x200B;设置为&#x200B;*[!UICONTROL Manually]*。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]**&#x200B;并将&#x200B;**[!UICONTROL Enable Terms and Conditions]**&#x200B;设置为&#x200B;*是*。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]**&#x200B;并配置[!DNL Braintree]。
1. 在店面，创建一个公司。
1. 在管理员中，转到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Companies]**。
1. 批准公司并允许&#x200B;**[!UICONTROL Purchase Orders]**。
1. 在前端，登录到帐户。
1. 将项目添加到购物车。
1. 使用&#x200B;**[!UICONTROL Purchase Order]**&#x200B;下订单。
1. 在客户仪表板中，单击&#x200B;**[!UICONTROL Purchase Orders]**&#x200B;选项卡。
1. 从新采购订单创建订单。 然后选择信用卡作为付款方式。
1. 同意条款和条件。
1. 下订单。

<u>预期的结果</u>：

当需要结帐的条款和条件时，您可以使用在线付款方法对批准的采购订单下达订单。

<u>实际结果</u>：

当需要结帐的条款和条件时，您不能使用在线付款方法对批准的采购订单下达订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
