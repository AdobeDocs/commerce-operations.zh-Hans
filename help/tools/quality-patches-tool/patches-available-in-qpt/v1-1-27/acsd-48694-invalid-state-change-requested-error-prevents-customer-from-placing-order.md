---
title: 'ACSD-48694：请求的状态更改无效错误阻止客户下订单'
description: 应用ACSD-48694修补程序以修复Adobe Commerce问题，该问题导致错误*请求的状态更改无效*阻止客户下订单。
feature: Admin Workspace, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-48694： *请求的状态更改无效*&#x200B;错误阻止客户下订单

ACSD-48694修补程序修复了以下问题：错误&#x200B;*请求的无效状态更改*&#x200B;阻止客户下订单。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27时，此修补程序可用。 修补程序ID为ACSD-48694。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.37-p4、2.4.1 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

错误&#x200B;*请求的状态更改无效*&#x200B;阻止客户下订单。

<u>重现步骤</u>：

1. 通过在`app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()`函数中包含`sleep()`而在`/estimate-shipping-methods`请求期间添加稍微延迟，因此，在结帐期间从送货步骤到付款步骤时，在`/shipping-information`之后完成`/estimate-shipping-methods`请求。
1. 将会话配置为使用&#x200B;*disable_locking： 1*&#x200B;设置的[!DNL Redis]。
1. 打开&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**&#x200B;并启用&#x200B;*[!UICONTROL Persistent Shopping Cart]*。
1. 以客户身份登录并将产品添加到购物车。
1. 让客户会话过期。 永久性Cookie和购物车仍然存在。
1. 现在，转到结帐，添加送货地址并导航到付款部分。
1. 返回主页或任何其他页面，然后使用客户帐户登录。
1. 让会话再次过期。
1. 现在，直接转到结账页面并导航到付款步骤。
1. 尝试下订单。

<u>预期的结果</u>：

* 没有错误。
* 已成功下订单，并显示&#x200B;*感谢*&#x200B;页面。

<u>实际结果</u>：

显示错误&#x200B;*请求的状态更改*&#x200B;无效，但已下达订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
