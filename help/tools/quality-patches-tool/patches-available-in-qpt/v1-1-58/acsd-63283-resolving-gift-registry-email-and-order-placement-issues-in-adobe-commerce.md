---
title: ACSD-63283：解决Adobe Commerce中的[!UICONTROL Gift Registry]电子邮件和订购问题
description: 应用ACSD-63283修补程序以修复Adobe Commerce的问题，该问题导致从[!UICONTROL Gift Registry]排序项目时出现异常，并确保[!UICONTROL Gift Registry Updates]仅包含正确的项目。
feature: Gift, Shopping Cart
role: Admin, Developer
exl-id: cff5b9e6-56ee-4df2-961a-6d90ec83c0c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-63283：解决Adobe Commerce中的[!UICONTROL Gift Registry]电子邮件和订购问题

ACSD-63283修补程序修复了从[!UICONTROL Gift Registry]中排序项目导致异常的问题，并确保[!UICONTROL Gift Registry Updates]仅包含正确的项目。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-63283。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

>[!NOTE]
>此修补程序将替换并扩展[ACSD-56280](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed) QPT修补程序。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

Adobe Commerce中的[!UICONTROL Gift Registry]功能受两个重要问题影响：

* 当客户从其[!UICONTROL Gift Registry]下达物料订单时，由于触发了异常，该流程将失败。
* 此外，发送给注册表所有者的[!UICONTROL Gift Registry Updates]电子邮件错误地包含来自所有礼品注册表的项目，而不是将更新限制在要更新的特定注册表中的项目。

<u>重现步骤</u>：

1. 创建两个产品：产品A和产品B。
1. 创建两个客户：客户A和客户B。
1. 以客户A身份登录并创建新[!UICONTROL Gift Registry]。
1. 导航到产品A的产品页面并将其添加到[!UICONTROL Wishlist]。 打开[!UICONTROL Wishlist Page]并使用[!UICONTROL Gift Registry]将产品A移动到[!UICONTROL Add to Gift Registry]。
1. 以客户B身份登录，创建新的[!UICONTROL Gift Registry]，然后将产品B添加到其中。
1. 作为客户B，通过电子邮件共享[!UICONTROL Gift Registry]： **[!UICONTROL My Account]> [!UICONTROL Gift Registry] >[!UICONTROL Share]**。
1. 以客户B的身份注销。
1. 单击电子邮件中收到的链接。 将产品B添加到[!UICONTROL Cart]并下订单。

<u>预期的结果</u>：

客户B仅会从其礼品注册处收到包含更新项目的电子邮件。

<u>实际结果</u>：

客户B收到包含所有礼品注册处商品的电子邮件。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
