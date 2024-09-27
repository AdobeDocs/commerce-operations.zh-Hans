---
title: 'ACSD-50345：签出期间出现reCAPTCHA问题'
description: 应用ACSD-50345修补程序以修复Adobe Commerce问题，该问题导致在下订单时和结账过程中reCAPTCHA v2和v3验证失败。
feature: Checkout, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-50345：在签出期间出现reCAPTCHA问题

ACSD-50345修补程序修复了在下订单和结账期间reCAPTCHA v2和v3验证失败的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.31时，此修补程序可用。 修补程序ID为ACSD-50345。 请注意，该问题已在Adobe Commerce 2.4.6中部分修复，并计划在Adobe Commerce 2.4.7中完全修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

**案例#1**

提交失败的付款后，Google reCAPTCHA v2未重新加载。

<u>重现步骤</u>

1. 配置&#x200B;**[!UICONTROL Google reCAPTCHA v2]** （*我不是机器人*）。
1. 启用&#x200B;**[!UICONTROL reCAPTCHA]**&#x200B;以进行签出。
1. 尝试在不单击&#x200B;**[!UICONTROL reCAPTCHA]**&#x200B;的情况下下订单。
1. 用户收到有关缺少的reCAPTCHA （*reCAPTCHA验证失败）的错误消息后，请重试*，单击&#x200B;**[!UICONTROL reCAPTCHA]**，然后尝试下订单。

<u>预期的结果</u>

订单的reCAPTCHA不正确。

<u>实际结果</u>

引发错误 — *reCAPTCHA验证失败，请重试*，*没有ID = 4*&#x200B;的此类购物车

**案例#2**

Google reCAPTCHA v3 Invisible在签出时不起作用，无法下订单。 未触发`PlaceOrder`事件。

<u>重现步骤</u>

1. 从&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**&#x200B;配置&#x200B;**[!UICONTROL reCAPTCHA v3 Invisible]**。
1. 启用&#x200B;**[!UICONTROL reCAPTCHA v3 Invisible]**&#x200B;以在&#x200B;**[!UICONTROL Storefront]**&#x200B;选项卡下签出/下订单。
1. 尝试使用[!UICONTROL Check/Money order]付款方式下订单。

<u>预期的结果</u>

订单应在&#x200B;**[!UICONTROL reCAPTCHA]**&#x200B;开启的情况下下达。

<u>实际结果</u>

单击&#x200B;**[!UICONTROL Place Order]**&#x200B;按钮后，该按钮将被禁用，并且不会再发生任何操作。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
