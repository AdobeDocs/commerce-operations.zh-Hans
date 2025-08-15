---
title: ACSD-61134：在结账工作流中自动取消选择[!UICONTROL Braintree Vault]付款方式
description: 应用ACSD-61134修补程序以解决在购物者通过取消选中*[!UICONTROL Braintree Vault]*复选框更新其帐单地址时，在结账工作流中自动取消选中*[!UICONTROL My billing and shipping address are the same]*付款方法的Adobe Commerce问题。
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134：在结账工作流中自动取消选择&#x200B;*[!UICONTROL Braintree Vault]*&#x200B;付款方式

ACSD-61134修补程序修复了以下问题：当购物者通过取消选中&#x200B;*[!UICONTROL Braintree Vault]*&#x200B;复选框更新其帐单地址时，在结账工作流中自动取消选择&#x200B;*[!UICONTROL My billing and shipping address are the same]*&#x200B;付款方式。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54时，此修补程序可用。 修补程序ID为ACSD-61134。 请注意，此问题计划在Adobe Commerce 2.4.7-beta1中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6-p7

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在结账工作流中自动取消选择&#x200B;*[!UICONTROL Braintree Vault]*&#x200B;付款方式。

<u>重现步骤</u>：

1. 在启用&#x200B;*[!DNL Braintree]*&#x200B;的情况下配置&#x200B;*[!UICONTROL Vault]*&#x200B;付款方法。
1. 结帐并在&#x200B;*[!UICONTROL Vault]*&#x200B;中保存卡片。
1. 查看其他产品。
1. 在&#x200B;*[!UICONTROL Shipping]*&#x200B;页面上，添加新的送货地址，以便您有两个地址可供选择。
1. 在&#x200B;*[!UICONTROL Payment]*&#x200B;页面上，选择您的付款方式并单击&#x200B;**[!UICONTROL My billing and shipping addresses are the same]**。

<u>预期的结果</u>：

所选的付款方式保持选定状态。

<u>实际结果</u>：

所选付款方式未选中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
