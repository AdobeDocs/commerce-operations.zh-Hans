---
title: ACSD-62952：店面中显示的礼品注册日期不准确
description: 应用ACSD-62952补丁以修复店面礼品注册日期显示不准确的Adobe Commerce问题。
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-62952：店面中显示的礼品注册日期不准确

ACSD-62952修补程序修复了店面中礼品注册日期显示不准确的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56时，此修补程序可用。 修补程序ID为ACSD-62952。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

共享礼品注册店面中显示的事件日期错误地显示为实际日期的前一天。

<u>重现步骤</u>：

1. 以客户身份登录到前端。
1. 在[!UICONTROL My Account]仪表板中，单击&#x200B;**[!UICONTROL Gift Registry]**。
1. 如果没有现有的注册表，请创建一个注册表并指定任何日期。
1. 将任意项目添加到购物车。
1. 在购物车页面中，单击&#x200B;**[!UICONTROL Add all items to Gift Registry]**。
1. 共享礼品注册表。

<u>预期的结果</u>：

礼品注册处显示正确的活动日期。

<u>实际结果</u>：

从邀请电子邮件中打开的礼品注册将活动日期显示为一天之前。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的升级和修补程序>应用修补程序。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
