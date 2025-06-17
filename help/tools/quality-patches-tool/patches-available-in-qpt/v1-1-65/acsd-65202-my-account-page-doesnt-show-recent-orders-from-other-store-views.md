---
title: ACSD-65202：“我的帐户”页不显示来自其他商店视图的最近订单
description: 应用ACSD-65202修补程序以修复Adobe Commerce问题，该问题导致“我的帐户”页面不显示同一商店中其他商店视图的最近订单。
feature: Orders, User Account
role: Admin, Developer
source-git-commit: 0af6ab4ef15e8aa56354886b341b70a080662eae
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# ACSD-65202： [!UICONTROL My Account]页面不显示来自其他商店视图的最近订单

ACSD-65202修补程序修复了&#x200B;**[!UICONTROL My Account]**&#x200B;页面不显示同一商店中其他商店视图的最近订单的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65时，此修补程序可用。 修补程序ID为ACSD-65202。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p12

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当您转到客户帐户页面（**[!UICONTROL My Account]**&#x200B;部分）时，您看不到其他商店视图中下达的最近订单。 但是，当您转到订单历史记录（第&#x200B;*[!UICONTROL My Orders]*&#x200B;部分）时，您会在两个商店视图中看到所有订单。

<u>重现步骤</u>：

1. 安装Adobe Commerce。
1. 在&#x200B;*管理员*&#x200B;面板中，创建一个新的商店视图，并以&#x200B;*秒*&#x200B;的形式输入其代码以标识该视图。
1. 创建简单产品并重新索引。
1. 创建客户帐户，并在代码为&#x200B;*default*&#x200B;的默认商店视图下订单。
1. 转到&#x200B;**[!UICONTROL My Orders]**&#x200B;页面，并检查该顺序在两个存储视图中是否均可见，例如：
1. 默认值： https://localhost/pub/default/sales/order/history/
1. 第二个：https://localhost/pub/second/sales/order/history/

1. 在两个应用商店视图中转到&#x200B;**[!UICONTROL My Account]**&#x200B;页面：
1. 默认值： https://localhost/pub/default/customer/account/
1. 第二个：https://localhost/pub/second/customer/account/

<u>预期的结果</u>：

您可以在“订单”页面上从两个商店视图中查看订单。 是同一家店，只是店面景色不同。

<u>实际结果</u>：

行为不一致。 订单不会显示在第二个商店视图中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
