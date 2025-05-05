---
title: ACSD-47920：即使[!UICONTROL Allow Guest Checkout]关闭，访客用户也可以通过REST API下订单
description: 应用ACSD-47920修补程序以修复Adobe Commerce问题，该问题导致即使在[!UICONTROL Allow Guest Checkout]关闭的情况下，也可以通过REST API作为访客用户下达订单。
feature: REST, Checkout, Orders
role: Admin
exl-id: 27c74803-a3f3-46bc-9eb8-8e2c72c30cd9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-47920：即使&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;关闭，访客用户也可以通过REST API下订单

ACSD-47920修补程序修复了以下问题：即使&#x200B;**[!UICONTROL Allow Guest Checkout]**&#x200B;处于关闭状态，也可以通过REST API以访客用户身份下达订单。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24时，此修补程序可用。 修补程序ID为ACSD-47920。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

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
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
