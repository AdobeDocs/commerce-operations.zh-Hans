---
title: 'ACSD-51149：计划的[!UICONTROL ImportExport]启用了[!UICONTROL Catalog Permissions]，使索引器失效'
description: 应用ACSD-51149修补程序以修复已启用了[!UICONTROL Catalog Permissions]的计划的[!UICONTROL ImportExport]使索引器失效的Adobe Commerce性能问题。
feature: Cache, Data Import/Export
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-51149：已启用[!UICONTROL Catalog Permissions]的计划[!UICONTROL ImportExport]使索引器失效

ACSD-51149修补程序修复了已启用了[!UICONTROL Catalog Permissions]的计划的[!UICONTROL ImportExport]使索引器失效的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.35时，此修补程序可用。 修补程序ID为ACSD-51149。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

计划的[!UICONTROL ImportExport]启用了[!UICONTROL Catalog Permissions]，使索引器失效。

<u>重现步骤</u>：

1. 启用&#x200B;*[!UICONTROL Catalog Permissions]*。
1. 将所有索引器设置为&#x200B;*[!UICONTROL Update by Schedule]*。
1. 创建一个简单的产品。
1. 通过&#x200B;**[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**&#x200B;导出此产品。
1. 下载导出的CSV，并将其放入`<AC root folder>/var/import`中。
1. 使用下载的CSV创建计划产品导入。
1. 运行完全重新索引。
1. 检查索引器的状态。 所有索引器都应处于&#x200B;*[!UICONTROL Ready]*&#x200B;状态。
1. 从网格运行创建的计划导入。
1. 重新检查索引器的状态。

<u>预期的结果</u>：

所有索引器都处于&#x200B;*[!UICONTROL Ready]*&#x200B;状态。

<u>实际结果</u>：

某些索引器处于&#x200B;*[!UICONTROL Reindex Required]*&#x200B;状态。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
