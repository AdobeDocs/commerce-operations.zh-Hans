---
title: Cron作业
description: 了解cron组和创建自定义cron作业。
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Cron作业

以下主题将讨论如何设置自定义cron作业以及可选的自定义cron组。 如果您的Commerce扩展需要定期运行计划任务，则可以使用这些主题来设置cron _作业_（计划任务），还可以选择同时运行自定义任务的cron _组_。

如果您使用Commerce提供的cron组，则无需定义自定义cron组；但是，如果您希望cron作业以其他计划运行，或者希望所有作业一起运行，则应当定义一个cron组

Commerce应用程序提供以下cron组：

- `default`，包含大多数cron作业
- `index`，它刷新[索引器](../cli/manage-indexers.md)
- `consumers`，运行消息队列[消费者](../cli/start-message-queues.md)
- 这些主题仅在Adobe Commerce中可用
   - `staging`，它运行[与暂存相关的](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/content-design/staging/content-staging)任务
   - `catalog_event`，它运行Target和购物车规则的任务
