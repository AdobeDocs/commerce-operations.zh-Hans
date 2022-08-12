---
title: “ [!UICONTROL Cron] 选项卡”
description: 了解 [!UICONTROL Cron] 选项卡 [!DNL Observation for Adobe Commerce].
source-git-commit: 3c1e50b3bff1bd2b2760e2e763173275161b0044
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# 的 [!UICONTROL Cron] 选项卡

此选项卡旨在快速隔离问题和导致崩溃问题的原因。

## [!UICONTROL Cron transaction duration in seconds]

![以秒为单位创建交易持续时间](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

的 **[!UICONTROL Cron transaction duration in seconds]** frame以秒为单位显示crons交易持续时间。 这将显示运行时间较长的事务。 更深入地了解APM将显示有关事务/操作可能运行的查询的更多详细信息。

## [!UICONTROL MySql Non-Sleeping Threads by Node]

![按节点划分的MySql非休眠线程](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

的 **[!UICONTROL MySql Non-Sleeping Threads by Node]** 框架按节点显示选定时间范围内的MySql非休眠线程。

## [!UICONTROL SQL Trace count by path]

![按路径的SQL跟踪计数](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

的 **[!UICONTROL SQL Trace count by path]** frame按路径查看MySql跟踪计数，这有助于跟踪选定时间范围内的SQL语句。

## [!UICONTROL Cron database call]

![Cron数据库调用](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

的 **[!UICONTROL Cron database call]** frame会查看在选定时间范围内调用数据库的cron数。

## [!UICONTROL Cron schedule table locks]

![Cron计划表锁定](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

的 **[!UICONTROL Cron schedule table locks]** frame会查看在选定时间范围内的cron计划表锁定。

## [!UICONTROL Cron schedule clean cron fired]

![Cron计划表锁定](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

的 **[!UICONTROL Cron schedule clean cron fired]** frame会查看在选定时间范围内清理的CRON数量。 如果此框架中未显示任何数据，则可能表示Cron运行正确时出现问题。 如果未清理cron作业计划，则cron将无法以最佳方式运行，并且运行可能需要更长的时间。

## [!UICONTROL Cron schedule clean records details table]

![Cron计划清理记录详细信息表](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

的 **[!UICONTROL Cron schedule clean records details table]** 表格提供了有关清理来自 `cron_schedule` 表。

## [!UICONTROL cron_schedule table updates]

![cron_schedule表更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

的 **[!UICONTROL cron_schedule table updates]** frame会查看在选定时间范围内cron计划表更新的次数。 删除或更新此表时的活动量较高，可能表示CRON存在问题。 此外，crons会在运行并完成时更新此表，因此，如果此表上没有活动且配置了cron，则crons可能会出现问题。

## [!UICONTROL Datastore Operations Tables]

![数据存储操作表](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

的 **[!UICONTROL Datastore Operations Tables]** 查看数据库表操作，包括 `SELECT`, `DELETE`和 `UPDATE` 跨选定的时间范围。 此帧显示对其运行频率最高的数据库表。
