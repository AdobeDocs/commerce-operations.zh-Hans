---
title: ' [!DNL Cron] 选项卡'
description: 了解 [!DNL Observation for Adobe Commerce]的 [!DNL Cron] 选项卡。
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# [!DNL Cron]选项卡

此选项卡试图快速隔离[!DNL cron]问题的问题和原因。

## [!UICONTROL Cron transaction duration in seconds]

![Cron事务持续时间（以秒为单位）](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

**[!UICONTROL Cron transaction duration in seconds]**&#x200B;框架显示[!DNL crons]事务持续时间（以秒为单位）。 这将显示运行时间较长的事务。 对APM的深入了解将显示有关事务/操作可能运行的查询的更多详细信息。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL非休眠Threads，按节点](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

**[!UICONTROL MySQL Non-Sleeping Threads by Node]**&#x200B;帧按节点显示所选时间范围内的MySQL非休眠线程。

## [!UICONTROL SQL Trace count by path]

按路径![&#128279;](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)列出的SQL跟踪计数

**[!UICONTROL SQL Trace count by path]**&#x200B;框架按路径查看MySQL跟踪计数，这有助于跟踪选定时间范围内的SQL语句。

## [!UICONTROL Cron database call]

![Cron数据库调用](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

**[!UICONTROL Cron database call]**&#x200B;帧查看选定时间范围内调用数据库的[!DNL crons]的数量。

## [!UICONTROL Cron schedule table locks]

![Cron计划表锁定](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

**[!UICONTROL Cron schedule table locks]**&#x200B;帧查看选定时间范围内的[!DNL cron]计划表锁定。

## [!UICONTROL Cron schedule clean cron fired]

![Cron计划表锁定](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

**[!UICONTROL Cron schedule clean cron fired]**&#x200B;帧查看选定时间范围内清理的[!DNL crons]的数量。 如果此帧中未显示任何数据，则可能表示[!DNL crons]运行不正常。 如果未清理[!DNL cron]作业计划，[!DNL crons]将无法以最佳方式运行，并且可能需要更长的时间才能运行。

## [!UICONTROL Cron schedule clean records details table]

![Cron计划清理记录详细信息表](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

**[!UICONTROL Cron schedule clean records details table]**&#x200B;表提供了有关在选定时间范围内从`cron_schedule`表中清除记录的作业的详细信息。

## [!UICONTROL cron_schedule table updates]

![cron_schedule表更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

**[!UICONTROL cron_schedule table updates]**&#x200B;帧查看选定时间范围内的[!DNL cron]个计划表更新数。 此表的删除或更新活动频繁可能表示[!DNL crons]存在问题。 此外，[!DNL crons]在它们运行并完成时更新此表，因此如果此表上没有活动并且配置了[!DNL crons]，则[!DNL crons]可能存在问题。

## [!UICONTROL Datastore Operations Tables]

![数据存储操作表](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

**[!UICONTROL Datastore Operations Tables]**&#x200B;在选定的时间范围内查看数据库表操作，包括`SELECT`、`DELETE`和`UPDATE`。 此框架显示操作频率最高的数据库表。
