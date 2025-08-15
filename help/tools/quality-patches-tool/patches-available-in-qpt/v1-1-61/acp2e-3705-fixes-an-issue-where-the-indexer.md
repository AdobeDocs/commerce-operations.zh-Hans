---
title: ACP2E-3705：在设置“MAGE_INDEXER_THREADS_COUNT”时，“indexer_update_all_views”cron执行失败
description: 应用ACP2E-3705修补程序以修复在设置“MAGE_INDEXER_THREADS_COUNT”时，“indexer_update_all_views”cron执行失败的Adobe Commerce问题。
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACP2E-3705：设置`indexer_update_all_views`时，`MAGE_INDEXER_THREADS_COUNT` cron执行失败

>[!NOTE]
>
>此修补程序取代了版本2.4.7及更高版本的[ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md)。

ACP2E-3705修补程序修复了在设置`indexer_update_all_views`时`MAGE_INDEXER_THREADS_COUNT` cron执行失败的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61时，此修补程序可用。 修补程序ID为ACP2E-3705。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当`indexer_update_all_views`设置为大于`MAGE_INDEXER_THREADS_COUNT`2 *的值时，* cron执行失败，具体影响启用了B2B的[!UICONTROL Customer Segments]索引器。

<u>重现步骤</u>：

1. 应用QPT修补程序[ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md)。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**。
1. 启用&#x200B;**[!UICONTROL Category Permissions]**。
1. 将以下索引器设置为&#x200B;**[!UICONTROL Update on Schedule]**&#x200B;模式：

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. 创建一些产品并将它们分配给类别。
1. 执行完全重新索引。
1. 转到类别并设置&#x200B;**[!UICONTROL Category Permissions]**。
1. 运行将`indexer_update_all_views`设置为`MAGE_INDEXER_THREADS_COUNT`8 *的* cron作业。

<u>预期的结果</u>：

重新索引已完成，且没有错误。

<u>实际结果</u>：

`indexer_update_all_views` cron作业遇到以下错误：

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的升级和修补程序>应用修补程序。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
