---
title: ACSD-62428：目录搜索索引中的库存状态错误
description: 应用ACSD-62428补丁程序，以修复当SKU不是可搜索的属性时，目录搜索索引中的"is_out_of_stock"值设置不正确的问题。
feature: Inventory, Catalog Management
role: Admin, Developer
source-git-commit: 633aa46886d65f45e8b503e3892e47bb24e40fc0
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428：目录搜索索引中的库存状态错误

ACSD-62428修补程序修复了以下问题：当SKU属性未设置为可搜索时，目录搜索索引中的`is_out_of_stock`值设置为不正确的值。 此修补程序在[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56中可用。修补程序ID为ACSD-62428。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6-p5

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当SKU未配置为可搜索属性时，目录搜索索引中的`is_out_of_stock`值设置为不正确的值，从而导致不准确的库存表示。

<u>重现步骤</u>：

1. 创建自定义[!UICONTROL Source]和自定义[!UICONTROL Stock]。
1. 创建三个简单产品并将其库存分配给自定义[!UICONTROL Source]。 将这些产品分配给类别。
1. 将&#x200B;*[!UICONTROL Inventory (MSI) Indexer]*&#x200B;设置为&#x200B;*[!UICONTROL Update on Save]*&#x200B;以便更轻松地复制。
1. 将&#x200B;*[!UICONTROL Source Item Status]*&#x200B;设置为&#x200B;*[!UICONTROL In Stock]*&#x200B;并分配&#x200B;*[!UICONTROL Quantity]*。
1. 保存产品。
1. 导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**，然后打开&#x200B;**[!UICONTROL SKU]**&#x200B;属性。
1. 将&#x200B;*[!UICONTROL Use In]*&#x200B;设置为&#x200B;*[!UICONTROL No]*。
1. 更改产品数量（确保未设置为0）。
1. 保存产品。

<u>预期的结果</u>：

`is_out_of_stock`值准确地反映了产品的库存状态，即使SKU不是可搜索属性也是如此。

<u>实际结果</u>：

`is_out_of_stock`值未正确设置为1，并且索引数据中不存在SKU属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
