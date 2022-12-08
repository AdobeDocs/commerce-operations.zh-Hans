---
title: “ [!DNL Cron] 选项卡”
description: 了解 [!DNL Cron] 选项卡 [!DNL Observation for Adobe Commerce].
source-git-commit: 38467ebd2ec29f9e1679182fb1ee7076d738664b
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 的 [!DNL Cron] 选项卡

此选项卡旨在快速隔离问题和原因 [!DNL cron] 问题。

## [!UICONTROL Cron transaction duration in seconds]

![以秒为单位创建交易持续时间](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

的 **[!UICONTROL Cron transaction duration in seconds]** 框架显示 [!DNL crons] 事务持续时间（以秒为单位）。 这将显示运行时间较长的事务。 更深入地了解APM将显示有关事务/操作可能运行的查询的更多详细信息。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![按节点划分的MySQL非休眠线程](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

的 **[!UICONTROL MySQL Non-Sleeping Threads by Node]** 框架按节点显示选定时间范围内的MySQL非休眠线程。

## [!UICONTROL SQL Trace count by path]

![按路径的SQL跟踪计数](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

的 **[!UICONTROL SQL Trace count by path]** frame按路径查看MySQL跟踪计数，这有助于跟踪选定时间范围内的SQL语句。

## [!UICONTROL Cron database call]

![Cron数据库调用](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

的 **[!UICONTROL Cron database call]** frame查看 [!DNL crons] 在选定的时间范围内调用数据库。

## [!UICONTROL Cron schedule table locks]

![Cron计划表锁定](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

的 **[!UICONTROL Cron schedule table locks]** 框架查看 [!DNL cron] 计划表在选定的时间范围内锁定。

## [!UICONTROL Cron schedule clean cron fired]

![Cron计划表锁定](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

的 **[!UICONTROL Cron schedule clean cron fired]** frame查看 [!DNL crons] 已在选定的时间范围内清理。 如果此帧中未显示任何数据，则可能表示 [!DNL crons] 正确运行。 如果 [!DNL cron] 作业计划未清理， [!DNL crons] 运行不会达到最佳状态，运行可能需要较长时间。

## [!UICONTROL Cron schedule clean records details table]

![Cron计划清理记录详细信息表](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

的 **[!UICONTROL Cron schedule clean records details table]** 表格提供了有关清理来自 `cron_schedule` 表。

## [!UICONTROL cron_schedule table updates]

![cron_schedule表更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

的 **[!UICONTROL cron_schedule table updates]** frame查看 [!DNL cron] 计划表会在选定的时间范围内进行更新。 在删除或更新此表时，活动很活跃，这可能表示 [!DNL crons]. 此外， [!DNL crons] 在运行并完成时更新此表，因此，如果此表中没有活动，并且 [!DNL crons] 已配置，可能 [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![数据存储操作表](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

的 **[!UICONTROL Datastore Operations Tables]** 查看数据库表操作，包括 `SELECT`, `DELETE`和 `UPDATE` 跨选定的时间范围。 此帧显示对其运行频率最高的数据库表。
