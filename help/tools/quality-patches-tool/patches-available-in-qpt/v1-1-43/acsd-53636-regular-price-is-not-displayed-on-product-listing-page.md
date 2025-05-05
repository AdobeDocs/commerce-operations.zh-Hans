---
title: ACSD-53636：[!UICONTROL Product Listing]页面上不显示常规价格
description: 应用ACSD-53636修补程序以修复Adobe Commerce问题，该问题导致在具有具有特价子产品的可配置产品的*[!UICONTROL Product Listing]*页面上不显示常规价格。
feature: Catalog Management, Products
role: Admin, Developer
exl-id: e6d66ae4-2c21-466a-b03c-a1f486e7fa29
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-53636：*[!UICONTROL Product Listing]*&#x200B;页面上不显示常规价格

ACSD-53636修补程序修复了具有具有特价子产品的可配置产品的&#x200B;*[!UICONTROL Product Listing]*&#x200B;页面上未显示常规价格的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43时，此修补程序可用。 修补程序ID为ACSD-53636。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于其子产品具有特殊价格的可配置产品，常规价格不显示在&#x200B;*[!UICONTROL Product Listing]*&#x200B;页面上。

<u>重现步骤</u>：

1. 登录到管理员并转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Catalog]**，然后创建或打开任何可配置的产品。
2. 打开子产品，并为所有或其中一个子产品添加特殊价格并保存该产品。
3. 转到前端并打开可配置产品的&#x200B;**[!UICONTROL Product Detail]**&#x200B;页面；在带有特殊价格的子产品的样本上，您将看到&#x200B;*[!UICONTROL Regular price]*&#x200B;脱机（预期）。
4. 转到前端并打开具有特殊价格的可配置产品的&#x200B;**[!UICONTROL Product Listing]**&#x200B;页面；查看可配置产品样本更改不会显示常规价格，这一点与&#x200B;*[!UICONTROL Product Detail Page]*&#x200B;和其他简单产品不同。

<u>预期的结果</u>：

在&#x200B;*[!UICONTROL Product Listing]*&#x200B;页面上，可配置产品显示其子产品的常规价格。

<u>实际结果</u>：

在&#x200B;*[!UICONTROL Product Listing]*&#x200B;页面上，可配置产品不显示其子产品的常规价格。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
