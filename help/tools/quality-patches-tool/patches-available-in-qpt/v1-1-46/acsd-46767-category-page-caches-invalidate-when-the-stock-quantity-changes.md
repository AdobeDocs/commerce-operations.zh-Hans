---
title: 'ACSD-46767：库存数量更改时，[!UICONTROL Category]页面缓存失效'
description: 应用ACSD-46767修补程序以修复在库存数量更改时，即使产品仍有库存，[!UICONTROL Category]页面缓存也会失效的Adobe Commerce问题。
feature: Cache, Products, Inventory
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-46767：库存数量更改时，[!UICONTROL Category]页面缓存失效

ACSD-46767修补程序修复了库存数量更改时[!UICONTROL Category]页面缓存失效的问题，即使产品仍然有库存。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46时，此修补程序可用。 修补程序ID为ACSD-46767。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

库存数量更改时，[!UICONTROL Category]页面缓存失效。

<u>重现步骤</u>：

1. 创建一些产品并将它们添加到同一类别。
1. 在店面中打开&#x200B;*[!UICONTROL Category]*&#x200B;页面以确保该页面已缓存。
1. 向类别&#x200B;*中的产品之一下订单（产品数量已更改，但产品仍有库存）*。
1. 再次打开店面上的[!UICONTROL Category]页面。

<u>实际结果</u>：

页面不会从缓存加载。 它会重新生成。

<u>预期结果</u>：

页面从缓存加载。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
