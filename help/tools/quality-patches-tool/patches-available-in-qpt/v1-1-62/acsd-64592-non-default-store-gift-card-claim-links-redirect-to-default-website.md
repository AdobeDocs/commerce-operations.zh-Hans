---
title: ACSD-64592：非默认商店礼品卡报销申请链接重定向到默认网站
description: 应用ACSD-64592修补程序以修复以下问题：在多网站设置中，从辅助（非默认）网站购买虚拟礼品卡时，电子邮件中的礼品卡代码链接具有默认网站URL。
feature: Gift, Products
role: Admin, Developer
exl-id: 1cc026c0-7487-48e8-a092-3e72085ca38a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-64592：非默认商店礼品卡报销申请链接重定向到默认网站

ACSD-64592修补程序修复了一个问题：在多站点环境中，如果从辅助（非主要）网站购买虚拟礼品卡，则包含礼品卡代码链接的电子邮件会将用户定向到默认网站的URL。 请注意，该问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在多网站设置中，从次要（非默认）网站购买虚拟礼品卡时，包含礼品卡代码链接的电子邮件会将用户引导至默认网站的URL。

<u>重现步骤</u>：

1. 创建辅助网站、商店和商店视图。
1. 为基本网站和辅助网站配置不同的基本URL。
1. 创建包含某些数量选项的虚拟礼品卡。
1. 在&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Gift Card Accounts]**&#x200B;处生成新的代码池。
1. 在辅助网站上订购礼品卡产品。
1. 在Commerce管理员中开具订单发票。
1. 检查&#x200B;*的“礼品卡代码”链接中的URL。您已从两封*&#x200B;电子邮件中收到礼物。

<u>预期的结果</u>：

礼品卡代码链接应具有指向第二个网站的链接。

<u>实际结果</u>：

礼品卡代码链接具有默认网站URL，即使订单位于第二个网站上也是如此。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：
* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
