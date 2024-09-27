---
title: '''ACSD-51857：''aggregate_sales_report_bestsellers_data''的慢cron作业影响性能'''
description: 应用ACSD-51857修补程序以修复Adobe Commerce问题，该问题导致慢速cron作业“aggregate_sales_report_bestsellers_data”影响大型“sales_order”和“sales_order_item”数据库表。
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51857： `aggregate_sales_report_bestsellers_data`的慢cron作业影响性能

ACSD-51857修补程序修复了慢速cron作业`aggregate_sales_report_bestsellers_data`影响大型`sales_order`和`sales_order_item`数据库表的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34时，此修补程序可用。 修补程序ID为ACSD-51857。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`aggregate_sales_report_bestsellers_data`在`sales_order`和`sales_order_item`数据库表上的Cron作业性能缓慢。

要解决此问题，为报表获取数据的主要数据查询已重写为更高效的表单。 现在，它使用子查询来确定数据子集。

为了使子查询尽可能快地运行，已为`sales_order`数据库表`SALES_ORDER_STORE_STATE_CREATED`添加了基于`store_id`、`state`和`created_at`列的新索引。

<u>先决条件</u>

确保每天有大量订单。

<u>重现步骤</u>

1. 执行`aggregate_sales_report_bestsellers_data` cron作业。
1. 检查&#x200B;**[!UICONTROL Bestsellers]**&#x200B;选项卡下的管理员仪表板中要显示的数据。

<u>预期的结果</u>：

**[!UICONTROL Configuration]**&#x200B;选项卡下的&#x200B;*[!UICONTROL Quantity per source]*&#x200B;不应为空。

<u>实际结果</u>：

**[!UICONTROL Configuration]**&#x200B;选项卡下的&#x200B;*[!UICONTROL Quantity per source]*&#x200B;为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
