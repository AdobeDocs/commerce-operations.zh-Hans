---
title: 'MDVA-37115：“仅剩下0个”通知显示在产品页面上'
description: MDVA-37115修补程序解决了在可配置产品页面上显示不必要的*仅剩下0*注意事项的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-37115。 请注意，Adobe Commerce 2.4.3中已修复此问题。
feature: Configuration, Products, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# MDVA-37115：产品页面上显示“仅剩下0个”通知

MDVA-37115修补程序解决了可配置产品页面上显示不必要的&#x200B;*仅剩下0*&#x200B;注意事项的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-37115。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署类型） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署类型） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

可配置产品页面上会显示不必要的&#x200B;*仅剩余0个*&#x200B;通知。

<u>先决条件</u>：

清单模块已安装。

<u>重现步骤</u>：

1. 创建具有少量选项的可配置产品。
1. 去前台。
1. 打开可配置产品页面并选择任意选项。

<u>预期的结果</u>：

产品页面上不显示&#x200B;*剩余0个*&#x200B;通知。

<u>实际结果</u>：

*剩余0个*&#x200B;通知显示在产品页面上。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查是否有可用于Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
