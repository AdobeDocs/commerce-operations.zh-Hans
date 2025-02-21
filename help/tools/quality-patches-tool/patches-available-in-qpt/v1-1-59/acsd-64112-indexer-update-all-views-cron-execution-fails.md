---
title: ACSD-64112：在设置“MAGE_INDEXER_THREADS_COUNT”时，“indexer_update_all_views”cron执行失败
description: 应用ACSD-64112修补程序以修复在设置“MAGE_INDEXER_THREADS_COUNT”时，“indexer_update_all_views”cron执行失败的Adobe Commerce问题。
feature: Catalog Management, B2B
role: Admin, Developer
source-git-commit: 544c7b9664ccc9204c2c0c78b103ad823e18ef7d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# ACSD-64112：设置`MAGE_INDEXER_THREADS_COUNT`时，`indexer_update_all_views` cron执行失败

ACSD-64112修补程序修复了在设置`MAGE_INDEXER_THREADS_COUNT`时`indexer_update_all_views` cron执行失败的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59时，此修补程序可用。 修补程序ID为ACSD-64112。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p10

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当`MAGE_INDEXER_THREADS_COUNT`设置为大于2的值时，`indexer_update_all_views` cron执行失败，具体影响启用了B2B的[!UICONTROL Customer Segments]索引器。

<u>重现步骤</u>：

1. 使用B2B安装干净的实例。
1. 启用&#x200B;**[!UICONTROL B2B Company]**&#x200B;和&#x200B;**[!UICONTROL Shared Catalog]**。
1. 创建类别。
1. 创建一些产品并将它们分配给类别。
1. 执行完全重新索引。
1. 将以下索引器设置为&#x200B;**[!UICONTROL Update on Schedule]**：

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. 转到后端并加载新创建的类别。
1. 单击&#x200B;**[!UICONTROL Category Permissions]**&#x200B;并为现有客户组创建&#x200B;**[!UICONTROL New Permission]**。
1. 确保`catalogpermissions_category`索引器有积压。 执行以下命令来验证这一点：

   ```
   bin/magento indexer:status
   ```

1. 在`env.php`中设置以下索引器线程计数：

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. 运行cron作业：

   ```
   bin/magento cron:run
   ```

<u>预期的结果</u>：

cron作业应可正常执行。

<u>实际结果</u>：

`indexer_update_all_views` cron作业遇到以下错误：

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 安装修补程序后所需的其他步骤

（本节为可选内容；在应用修补程序后，可能需要执行一些步骤来修复此问题。） 

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
