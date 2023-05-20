---
title: Adobe Commerce整合策略
description: 檢閱Adobe Commerce實作的整合策略和選項。
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Adobe Commerce整合策略

整合平台的能力是「不可商量」的。 企業希望他們的電子商務平台可以從各種接觸點進行存取，並順暢地整合到他們的技術系統中，尤其是他們的ERP。 客製化、全球擴充能力及經濟實惠，也是最終購買平台的重要一環。

高效能的GraphQL API、全面的REST API，以及Adobe Commerce與其他系統或服務之間的批次檔案匯入，都支援適用於店面和後端系統的整體整合方法。

Adobe Commerce GraphQL API提供全方位的店面覆蓋範圍，可用來與其他店面整合，包括：

- Adobe Experience Manager和Bloomreach等數位體驗平台(DXP)
- Drupal和WordPress等內容管理系統(CMS)
- Adobe Commerce、PWA Studio和Vue Storefront等現代自訂店面應用程式

GraphQL提供高效率、通道專屬的回應、避免過度擷取資料，以及敏捷部署新接觸點功能。 它通常也可以與行動原生應用程式、POS、IoT、社交頻道和直播串流商業頻道(例如Facebook、Google、Instagram、微信和TikTok)等銷售頻道整合。

Adobe Commerce REST API提供完整的系統設定涵蓋範圍和資料管理功能，包括產品和目錄、購物車、報價和結帳、客戶、帳戶和公司，以及訂單和退貨。 REST API支援大量作業、多種驗證模式和精細授權，因此REST API通常選擇與企業系統整合，包括：

- SAP等企業資源規劃(ERP)系統
- Akeneo等產品資訊管理(PIM)系統
- Salesforce等客戶關係管理(CRM)系統
- 訂單管理系統(OMS)，例如MOM、Manhattan和SAP
- 倉儲管理系統(WMS)或第三方物流(3PL)，例如Oracle、NetSuite和SAP WM
- 設定、定價、報價(CPQ)，如SalesforceCPQ
- AdobeDAM等數位資產管理(DAM)。

批次檔案匯入也被視為整合企業系統（例如ERP和PIM）的好選擇，因為這類資料不會經常變更，而且您通常在排程檔案匯入時會有更好的效能。 因此，批次檔案匯入通常選擇每日/每週和每月完整資料同步進行大量資料同步，而REST API則選擇用於增量資料變更同步，以獲得更好的效能。 這也只會被視為排程工作，但可視業務需求經常進行（可能每15分鐘至1小時一次）。

## 整合選項

Adobe Commerce提供三種彈性的整合選項：

- 透過預先建立的聯結器進行直接的系統對系統整合。 有些系統可能在Adobe Commerce Marketplace或自己的網站上已有Adobe Commerce擴充功能。

- 透過自訂中介進行系統間整合。 所部署的自訂中介軟體解決方案將用於流程資料對應、翻譯和管理。

- 透過iPaaS (Integration Platform-as-a-Service，也稱為EAI (Enterprise Application Integration Platform)，例如Mulesoft、Boomi和Software AG，進行系統到系統的整合。

![Adobe Commerce整合選項](../../assets/playbooks/integration-options.svg)

雖然通常需要即時整合，但在某些情況下並不需要。 Adobe Commerce原生支援 [!DNL RabbitMQ] 作為訊息匯流排來啟用非同步處理，建議用於某些不需要即時交換的資料，而是使用批次檔案交換或REST批次資料處理API進行更新以非同步處理。
