---
title: ACSD-52786：目录规则*[!UICONTROL SKU is]*适用于以SKU开头的所有产品
description: 应用ACSD-52786修补程序以修复Adobe Commerce问题，该问题导致目录规则条件*[!UICONTROL SKU is]*适用于以给定SKU开头的所有产品。
feature: Price Rules
role: Admin
exl-id: 668d5f16-18a9-4054-aa6e-1fb8fa211373
source-git-commit: f6abbbb28a3077f7bf26a393388c5059fcd8c599
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52786：目录规则“*[!UICONTROL SKU is]*”适用于以SKU开头的所有产品

ACSD-52786修补程序修复了目录规则条件&#x200B;*[!UICONTROL SKU is]*&#x200B;适用于以给定SKU开始的所有产品的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.35时，此修补程序可用。 修补程序ID为ACSD-52786。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

目录规则条件&#x200B;*[!UICONTROL SKU is]*&#x200B;适用于以给定SKU开始的所有产品。

<u>重现步骤</u>：

1. 创建两个产品，一个带有SKU“24”，另一个带有SKU“24-MB01”。
1. 导航到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**。
1. 应用以下条件：
   * 这些条件中的&#x200B;*[!UICONTROL If **&#x200B;全部&#x200B;**为** TRUE **]*： *[!UICONTROL SKU is 24]*
1. 在操作中设置任何折扣金额。
1. 单击&#x200B;**[!UICONTROL Save and Apply]**。
1. 刷新缓存。
1. 去店面看看24-MB01的价格。

<u>预期的结果</u>：

目录规则仅应用于SKU等于24的单个产品。

<u>实际结果</u>：

目录规则条件&#x200B;*[!UICONTROL SKU is]*&#x200B;适用于以给定SKU开始的所有产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
