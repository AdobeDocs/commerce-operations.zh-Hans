---
title: Cron作业
description: 了解cron组以及如何在Adobe Commerce中创建自定义cron作业。 发现计划任务设置和cron组配置。
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '179'
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
  - `staging`，它运行[与暂存相关的](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging)任务
  - `catalog_event`，它运行Target和购物车规则的任务
