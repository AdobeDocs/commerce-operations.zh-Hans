---
title: Cron作业
description: 了解cron组和创建自定义cron作业。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Cron作业

这些主题讨论了如何设置自定义cron作业和（可选）自定义cron组。 如果您的商务扩展要求定期运行计划任务，则可以使用这些主题设置触发器 _作业_ （计划任务）和（可选） _群组_，可同时运行自定义任务。

如果您使用商务提供的cron群组，则无需定义自定义cron群组；但是，如果您希望cron作业以不同的时间表运行，或者希望它们全部一起运行，则应该定义cron组

商务应用程序提供了以下群组：

- `default`，其中包含大多数cron作业
- `index`，刷新 [索引器](../cli/manage-indexers.md)
- `consumers`，运行消息队列 [消费者](../cli/start-message-queues.md)
- 这些主题仅在Adobe Commerce中可用
   - `staging`，运行 [与暂存相关](https://docs.magento.com/user-guide/cms/content-staging.html) 任务
   - `catalog_event`，可为target和购物车规则运行任务
