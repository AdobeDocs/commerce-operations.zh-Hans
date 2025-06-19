---
title: ACSD-53176：具有“为之一”条件的产品规则不匹配
description: 应用ACSD-53176修补程序以修复Adobe Commerce问题，该问题导致相关的产品规则“是”条件无法正常用于“要匹配的产品”。
feature: Marketing Tools
role: Admin
exl-id: 8260c6ac-3ca2-4361-9e36-a8a58468fa95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-53176：具有`is one of`条件的产品规则不匹配

ACSD-53176修补程序修复了相关产品规则`is one of`条件无法正确工作的问题，无法使&#x200B;**产品匹配**。 安装[!DNL Quality Patches Tool (QPT)] 1.1.36时，此修补程序可用。 修补程序ID为ACSD-53176。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

相关产品规则`is one of`条件无法正确工作，无法匹配产品&#x200B;****。

<u>重现步骤</u>：

1. 创建3-4个产品。
1. 创建新的相关产品规则。

   设置规则以匹配两个或更多产品：
   * `SKU is one of "S1,S2".`

   设置规则以显示两个或多个项目：
   * `Product SKU is one of constant value "S2,S3".`

1. 打开店面上的S1产品。

<u>预期的结果</u>：

相关产品“S2”和“S3”会同时显示在产品页面“S1”和“S2”上。

<u>实际结果</u>：

相关产品不会显示在产品页面上。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
