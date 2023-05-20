---
title: Cron工作
description: 瞭解cron群組和建立自訂cron工作。
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Cron工作

這些主題討論如何設定自訂cron工作以及可選的自訂cron群組。 如果您的Commerce擴充功能需要定期執行排程工作，您可以使用這些主題來設定cron _工作_ （排程工作）和選擇性cron _群組_，可同時執行自訂工作。

如果您使用Commerce提供的cron群組，則不必定義自訂cron群組；但是，如果您希望cron工作以不同的排程執行，或希望它們一起執行，則您應該定義cron群組

Commerce應用程式提供下列cron群組：

- `default`，其中包含大多數cron工作
- `index`，會重新整理 [索引子](../cli/manage-indexers.md)
- `consumers`，會執行訊息佇列 [消費者](../cli/start-message-queues.md)
- 這些主題僅適用於Adobe Commerce
   - `staging`，會執行 [與測試相關](https://docs.magento.com/user-guide/cms/content-staging.html) 任務
   - `catalog_event`，會執行target和購物車規則的工作
