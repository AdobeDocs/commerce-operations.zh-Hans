---
title: ACSD-52095：导出CSV时管理股票值错误
description: 应用ACSD-52095修补程序以修复导出CSV时Adobe Commerce产品管理库存值错误的问题。
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-52095：导出CSV时[!UICONTROL Manage Stock]值错误

ACSD-52095修补程序修复了在导出CSV时产品`manage_stock`值错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.35时，此修补程序可用。 修补程序ID为ACSD-52095。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品导出后，CSV文件中的`manage_stock`值未正确设置为0。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**&#x200B;并设置&#x200B;**[!UICONTROL Manage Stock]** = *[!UICONTROL No]*。
1. 创建新产品并保存它。
1. 转到&#x200B;**[!UICONTROL System]** > **[!UICONTROL Export]**。
1. 选择&#x200B;*[!UICONTROL Entity Type]* = *[!UICONTROL Products]*&#x200B;并导出产品。
1. 检查生成的CSV文件： `manage_stock` = 0， `use_config_manage_stock` = 1。
1. 再次转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**，并设置&#x200B;**[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*。
1. 转到&#x200B;**系统** > **导出**。
选择&#x200B;*[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*。
1. 检查生成的CSV文件： `manage_stock` = 0， `use_config_manage_stock` = 1。
1. 在管理员中打开产品，转到&#x200B;**[!UICONTROL Advanced Inventory]**&#x200B;并检查&#x200B;**[!UICONTROL Manage Stock]**&#x200B;值。

<u>预期的结果</u>

为产品启用&#x200B;**[!UICONTROL Manage Stock]**&#x200B;时，其值为&#x200B;*1*。

<u>实际结果</u>

为产品启用&#x200B;**[!UICONTROL Manage Stock]**&#x200B;时，其值为&#x200B;*0*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans>)。
