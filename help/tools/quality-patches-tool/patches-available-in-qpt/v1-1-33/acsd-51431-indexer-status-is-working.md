---
title: 'ACSD-51431：索引器状态为*[!UICONTROL Working]*，即使更改日志中没有条目'
description: 应用ACSD-51431修补程序以修复索引器状态为*[!UICONTROL Working]*的Adobe Commerce问题，即使更改日志中没有条目。
feature: Logs, Price Indexer
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-51431：即使更改日志中没有条目，索引器状态为&#x200B;*[!UICONTROL Working]*

ACSD-51431修补程序修复了索引器状态为&#x200B;*[!UICONTROL Working]*&#x200B;的性能问题，即使更改日志中没有条目。 安装[!DNL Quality Patches Tool (QPT)] 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51431。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

索引器状态为&#x200B;*[!UICONTROL Working]*，即使更改日志中没有条目。

<u>重现步骤</u>：

1. 将&#x200B;**[!UICONTROL indexers]**&#x200B;设置为[!UICONTROL Update on Schedule]。
1. 将cron作业配置为每分钟运行一次。
1. 同时保存对不同产品的更改。
1. 在几分钟后运行`bin/magento indexer:status`。

<u>预期的结果</u>：

更改已处理，索引器处于&#x200B;*[!UICONTROL Ready]*&#x200B;状态。 *[!UICONTROL Schedule]*&#x200B;状态为&#x200B;*[!UICONTROL idle (0 in the backlog)]*。

<u>实际结果</u>：

更改已处理，索引器处于&#x200B;*[!UICONTROL Ready]*&#x200B;状态。 但是，*[!UICONTROL Schedule]*&#x200B;状态显示&#x200B;*[!UICONTROL working (0 in the backlog)]*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
