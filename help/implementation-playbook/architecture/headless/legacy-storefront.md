---
title: 耦合式店面架構
description: 瞭解在Headless Adobe Commerce架構中，耦合店面意味著什麼。
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# 耦合（舊版） Adobe Commerce店面架構

目前大多數商業客戶的預設部署選項包括：

- 100%功能支援B2B和B2C
- 可快速部署/自訂的成熟參考主題(Luma)
- 成熟的SI合作夥伴實作專業知識
- 與商業功能完全相容，例如頁面產生器或測試與預覽
- 與Adobe Commerce Marketplace中的擴充功能廣泛相容

![顯示耦合Adobe Commerce店面架構的圖表](../../../assets/playbooks/coupled-storefront-architecture.svg)

## 舊式店面的缺點

- **非Headless** — 整體式Adobe Commerce應用程式的所有部分。 前端和後端之間沒有業務邏輯和流程分離。

- **不PWA** — 雖然佈景主題反應靈敏，但網站效能遠遠落後於同級最佳PWA。

- **前端架構(Adobe Commerce UI元件)**—Adobe Commerce/PHP專家，在舊版店面基礎上進行構建。

在介紹Headless選項之前，讓我們先從更熟悉的店面架構開始。 如果Headless是分離的，這將會是耦合的店面架構，最常見的是我們的Luma示範。

這是店面功能與核心商務服務緊密整合的位置，不會由該GraphQL API層分隔。 因此，該主題結合了大量商業邏輯。 此方法不是Headless，也不是PWA。

這是商家目前最常使用的選項，因為它透過B2B和B2C Commerce功能提供100%功能支援。 社群對此很熟悉，周圍有成熟的專業生態系統，而且與Adobe Commerce Marketplace擴充功能有廣泛的相容性。

然而，它缺乏我們先前所談到的優點。 若不分離圖層，進行變更時，會有許多相依性和可能的失敗點。 它不如實作良好的PWA來得好，如果商家沒有在Adobe Commerce或PHP開發方面的專業知識，他們就必須去尋找這些資源。
