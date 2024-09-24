---
title: “ACSD-45049：客户‘必需’属性设置不适用于管理员中的网站范围”
description: 应用ACSD-45049修补程序以修复客户“[!UICONTROL Is required]”属性无法按照Admin中的网站范围正确覆盖的Adobe Commerce问题。
feature: Attributes, Customers
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-45049：客户&#x200B;*[!UICONTROL Is required]*&#x200B;属性设置无法按管理员中的网站范围使用

ACSD-45049修补程序修复了客户&#x200B;*[!UICONTROL Is required]*&#x200B;属性设置无法按照Admin中的网站范围正确工作的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-45049。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p7和2.4.5 - 2.4.5-p9

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

按照管理员中的网站作用域，客户&#x200B;*[!UICONTROL Is required]*&#x200B;属性设置无法正常工作。

<u>重现步骤</u>：

1. 创建两个网站。
1. 打开&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**。
1. 创建新属性，设置&#x200B;**[!UICONTROL Is value required]** = *否*。
1. 切换到默认网站，并更改&#x200B;**[!UICONTROL Is value required]** = *是*。 另一个网站具有默认值。
1. 从管理员中为非默认网站创建新客户。

<u>预期的结果</u>：

对于非默认网站，属性不是必需的。

<u>实际结果</u>：

* 在Admin中创建客户时，非默认网站需要属性。
* 在店面注册客户时，非默认网站不需要属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
