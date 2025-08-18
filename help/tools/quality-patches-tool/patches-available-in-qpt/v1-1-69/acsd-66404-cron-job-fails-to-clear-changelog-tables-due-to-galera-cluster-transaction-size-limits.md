---
title: ACSD-66404：由于 [!DNL Galera Cluster] 事务大小限制，Cron作业无法清除changelog表
description: 应用ACSD-66404修补程序以修复Adobe Commerce问题，该问题导致cron作业无法清除changelog表并在这些表中出现大量数据时导致 [!DNL Galera Cluster] 问题。
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 42bd5934782ca65b891a36f61102083356c92e59
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66404：由于[!DNL Galera Cluster]事务大小限制，Cron作业无法清除changelog表

ACSD-66404修补程序修复了cron作业无法清除changelog表的问题，该问题在处理大量数据时导致[!DNL Galera Cluster]问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-66404。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p6、2.4.7-p6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

Cron作业未清除changelog表，并在这些表中出现大量数据时导致[!DNL Galera Cluster]问题。

<u>重现步骤</u>：

1. 使用性能配置文件生成大量产品。
1. 为系统中的所有产品执行批量更新，因此`inventory_cl`数据库表中有许多条目。
1. 运行`indexer_clean_all_changelogs` cron作业。

<u>预期的结果</u>：

`indexer_clean_all_changelogs` cron作业能够在多个删除查询中对大型changelog （10 GB以上）执行changelog清理，而不会导致[!DNL Galera Cluster]问题。

<u>实际结果</u>：

`indexer_clean_all_changelogs` cron作业在单个删除查询中对大型changelog （10 GB以上）执行changelog清理，导致[!DNL Galera Cluster]问题。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： Tools指南中用于优质修补程序的Self-service工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
