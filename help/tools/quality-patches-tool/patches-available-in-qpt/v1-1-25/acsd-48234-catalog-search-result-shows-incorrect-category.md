---
title: ACSD-48234：启用[!UICONTROL Display Out of Stock Products]时，目录搜索结果类别项计数不正确
description: Adobe Commerce应用ACSD-48234修补程序以修复以下问题：启用[!UICONTROL Display Out of Stock Products]选项后，目录搜索结果显示错误的类别项计数。
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
exl-id: c177f12d-2db5-48e2-8f88-ff589cea4dd4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48234：目录搜索结果显示启用的类别项计数&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;不正确

ACSD-48234修补程序解决了启用&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;选项时，目录搜索结果显示不正确的类别项目计数的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25时，此修补程序可用。 修补程序ID为ACSD-48234。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。


## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;选项时，目录搜索结果显示的类别项计数不正确。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;并打开&#x200B;**[!UICONTROL color]**&#x200B;属性。
1. 添加两个选项，例如橙色和绿色。 保存属性。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**&#x200B;并将&#x200B;**[!UICONTROL color]**&#x200B;属性添加到&#x200B;**[!UICONTROL Default]**&#x200B;属性集。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]**&#x200B;并将&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;设置为&#x200B;_是_。
1. 创建类别“cat1”。
1. 创建两个产品：
   1. 名称：prod1，颜色：橙色，类别：cat1。
   1. 名称：prod2，颜色：绿色，类别：cat1。
1. 打开店面上的cat1类别。
1. 在分层导航中选择橙色。

<u>预期的结果</u>：

只显示prod1产品。

<u>实际结果</u>：

此时会显示prod1和prod2产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
