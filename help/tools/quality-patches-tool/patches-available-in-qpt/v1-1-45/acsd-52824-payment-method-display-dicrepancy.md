---
title: ACSD-52824：为公司客户显示的已禁用付款方法
description: 应用ACSD-52824修补程序以修复Adobe Commerce问题，该问题导致尽管公司设置中禁用了 [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] 付款方法，但仍向公司客户显示。
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 39d67de6-1796-4067-ae7a-ef17fcf794e5
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-52824：为公司客户显示的已禁用付款方法

ACSD-52824修补程序修复了在公司设置中禁用[!DNL PayPal Express]、[!DNL Google Pay]和[!DNL Apple Pay]付款方法后仍会向公司客户显示的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45时，此修补程序可用。 修补程序ID为ACSD-52824。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

为公司客户显示禁用的付款方法。

<u>重现步骤</u>：

1. 配置并启用[!DNL PayPal Express Checkout]。 导航到&#x200B;**[!UICONTROL Basic Settings]** >选择&#x200B;**[!DNL PayPal Express Checkout]**&#x200B;并将&#x200B;**[!UICONTROL Display on Shopping Cart]**&#x200B;的选项设置为&#x200B;*是*。
1. 通过[!DNL Braintree]配置[!DNL Braintree]并启用[!DNL Apple Pay]和[!DNL Google Pay]。
1. 导航到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Companies]**&#x200B;并创建新公司。
1. 单击&#x200B;**[!UICONTROL Advanced Settings]**，找到&#x200B;**[!UICONTROL Applicable Payment Methods]**&#x200B;并选择&#x200B;**[!UICONTROL Selected Payment Methods]**。
1. 在&#x200B;**[!UICONTROL Selected Payment Methods]**&#x200B;下，选择已启用且未与&#x200B;*[!DNL PayPal Express Checkout]*、*[!DNL Apple Pay]*&#x200B;或&#x200B;*[!DNL Google Pay]*&#x200B;关联的付款方法。 例如，选择&#x200B;**[!UICONTROL Check/Money Order]**。
1. 选择适当的付款方法后，创建一个新客户并将它们与之前创建的公司关联。
1. 使用与公司关联的客户帐户登录，然后继续将商品添加到购物车。
1. 在结账过程中，请注意迷你购物车、购物车和支付步骤。

<u>预期的结果</u>：

来自[!DNL PayPal]和[!DNL Braintree]的付款选项在迷你购物车和购物车中不可见。

<u>实际结果</u>：

来自[!DNL PayPal]和[!DNL Braintree]的付款选项在迷你购物车和购物车中仍然可见。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
