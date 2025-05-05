---
title: 'ACSD-50817：优化cron作业sales_clean_quotes以更快地运行'
description: 应用ACSD-50817修补程序以优化cron作业“sales_clean_quotes”，以便通过在报价表的“store_id”和“updated_at”列中添加复合索引而更快地运行。
feature: Quotes
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-50817：优化cron作业`sales_clean_quotes`以更快地运行

ACSD-50817修补程序通过为引号表中的`store_id`和`updated_at`列添加复合索引，优化了cron作业`sales_clean_quotes`的运行速度。 安装[!DNL Quality Patches Tool (QPT)] 1.1.31时，此修补程序可用。 修补程序ID为ACSD-50817。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

cron作业`sales_clean_quotes`太慢。 使用此修补程序，已通过在引号表的`store_id`和`updated_at`列中添加复合索引而优化该修补程序，使其运行得更快。

<u>重现步骤</u>：

1. 生成50-80M引号，并将`updated_at`设置为小于30天的周期。
1. 在报价表上运行cron作业`sales_clean_quotes`或以下查询：

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>预期的结果</u>

通过在报价表的`store_id`和`updated_at`列中添加复合索引，已优化Cron作业`sales_clean_quotes`以更快地运行。

<u>实际结果</u>

查询速度太慢。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
