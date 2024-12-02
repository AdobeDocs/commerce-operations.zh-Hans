---
title: ACSD-59229：由于过时的XMagento变化值而导致客户组数据分配错误
description: 应用ACSD-59229修补程序以修复Adobe Commerce问题，该问题导致与客户组相关的信息被保存在错误的区段中，因为请求中的X-Magento-Vary值已过期。
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: c039c114-d920-4b05-b5e9-3e9b73490ee0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-59229：由于过时的XMagento变化值而导致客户组数据分配错误

Magento ACSD-59229修补程序修复了客户组相关信息因请求中的过时X-Request-Vary值而被保存在错误区段中的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-59229。 请注意，此问题已在2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于请求中的XMagentoVary值已过期，因此将客户组相关信息保存在错误的区段中。

<u>先决条件</u>：

确保已安装包含示例数据的Adobe Commerce B2B并配置了[!DNL Varnish]。

<u>重现步骤</u>：

1. 为[!DNL SKU 24-MB01]设置高级定价：
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]：
      * *批发* = *$200*
      * *零售商* = *$30*

1. 创建两个客户帐户。
1. 将两个客户分配给&#x200B;**批发**&#x200B;组。
1. 打开两个不同的浏览器会话并与每个客户登录。
1. 导航到每个客户的&#x200B;**[!UICONTROL 24-MB01]**&#x200B;产品页面，并验证显示的价格是否为&#x200B;*$200*。
1. 将其中一个客户的客户组更改为&#x200B;**零售业**。
1. 使用以下命令清除缓存： `bin/magento cache:flush full_page`。
1. 刷新每个客户的产品页面。

<u>预期的结果</u>：

1. 零售客户可以看到产品的正确价格&#x200B;*$30*。
1. 批发客户可以看到产品的&#x200B;*$200*&#x200B;的正确价格。

<u>实际结果</u>：

1. 零售客户可以看到产品的正确价格&#x200B;*$30*。
1. 批发客户看到产品的&#x200B;*$30*（零售价）的价格不正确。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
