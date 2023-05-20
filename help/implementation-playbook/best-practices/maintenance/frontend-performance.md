---
title: 稽核前端效能
description: 透過使用網站效能工具稽核Adobe Commerce店面作業，找出並解決對網站效能有負面影響的問題。
role: Admin, User, Developer
feature: Best Practices
feature-set: Commerce
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# 前端效能的最佳實務

使用網頁效能工具來檢查Adobe Commerce商店的前端效能。
這些工具會使用各種量度，提供強大的分析和建議，以改善線上商店的效能。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 檢查前端效能

若要檢查網站商店的前端效能：

1. 使用Web效能工具稽核前端效能，例如：

   - **[Google燈塔](https://web.dev/measure/)**— Lighthouse針對效能、協助工具、漸進式網頁應用程式、SEO等專案進行稽核。 如需執行Lighthouse的不同方式的詳細資訊，請參閱 [Lighthouse概述](https://developer.chrome.com/docs/lighthouse/overview).)
   - **[Google PageSpeed深入分析](https://pagespeed.web.dev/)**— PageSpeed Insights可快速傳送詳細報告，說明網頁效能緩慢的原因，並提供修正建議。

1. 檢閱稽核報告並實作所提出的建議以改善商店效能。

## 其他資訊

- [管理員使用者的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用CLI進行索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [適用於開發人員的索引概觀](https://developer.adobe.com/commerce/php/development/components/indexing/)
