---
title: 自行託管概述
description: 瞭解自託管最佳實務，供您考慮。 主題涵蓋安全性元素、災難回覆等等。 這些主題旨在協助已決定託管自己Adobe Commerce版本的公司。 呈現的專案並非全包容，但應提供各種良好的概念，以推廣安全、穩定且可復原的網站。
landing-page-description: 瞭解自行託管Adobe Commerce時應考量的一些概念和事項。
short-description: 瞭解自行託管Adobe Commerce的策略和概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 63f552f3-836c-4a07-96c3-c0e00614fe39
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# 自行託管Adobe Commerce概述

在考慮改用Adobe Commerce等電子商務平台時，您可擁有眾多選擇。 但是，這些選項會帶來額外的成本、風險和負債需要考慮。 託管Commerce網站可使用封裝解決方案完成，例如 [雲端基礎結構上的Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}，基礎架構、伺服器、電子郵件、SSL憑證等已預先設定且可供使用。 在雲端基礎結構上尋找Adobe Commerce等良好的託管解決方案，可讓整個程式更輕鬆，有極具吸引力的原因可讓您自行託管Commerce網站。 在隨附的頁面中，有許多主題可針對自行託管所提供的服務、技巧和概念提供深入分析和指引。 此處的資訊並非詳盡無遺，且預期您不應該實作每個建議。 不過，這些文章可協助您瞭解讓Adobe Commerce自行託管儘可能穩定且安全的構想和概念。

如果您沒有在雲端基礎結構上使用Adobe Commerce，則使用的術語是自行託管或內部部署，甚至內部部署。 內部部署不僅是指在公司擁有的大樓內的資料中心。 此辭彙代表Adobe Commerce未在其基礎結構上管理支援的任何專案。 有些託管公司是專為Adobe Commerce服務的，這類公司也視為自行託管或內部部署。

關於Adobe Commerce和Magento開放原始碼，大多數建議和提示都適用於任一版本。 即使它可能不會直接說明，但可預期適用於兩者。 在有關Adobe Commerce的自託管選項的主題中，會同時考慮兩個版本。 最後，大多數主題都與 [雲端基礎結構上的Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} 已選取作為託管提供者。

## 術語層級設定

以下辭彙在整篇Experience League文章中都很常用，在與DevOps團隊交談時以及搭配公司支援人員使用時：

* **DevOps** 是一個術語，用來描述處理伺服器設定、設定、管理、SSL憑證的團隊，以及有關用於執行Adobe Commerce網站的實際伺服器和服務的所有其他內容。 此辭彙用於協助指定開發人員的責任通常何時結束，以及基礎架構團隊的分級和支援從何處開始。

* **安全性概念** 包含數個主題和考量事項，以利在伺服器上建立Adobe Commerce程式碼基底、檔案和檔案系統，以及任何可減少許多已知利用漏洞模式的攻擊面的設定或更新。

* **監控工具** 涵蓋數個監控Adobe Commerce網站的現有工具及服務。 這些工具有時可提供如何改善的秘訣，或揭示問題和安全性弱點。

* **災難回覆** 有助於提供某些概念和考量事項，以因應專案損毀或被利用的不幸事件。

* **效能提示** 提供一些讓Adobe Commerce應用程式儘可能發揮效能的專業秘訣和指引。

* **演員錯誤** 是用來表示有人或團隊嘗試進行惡意或未經授權的動作。 這不限於商務應用程式，也延伸至基礎結構或與網站相關的任何元件。

* **Web應用程式防火牆** (WAF)可協助您檢視商務應用程式的每個請求標題，並封鎖已知模式和剝削。 通常WAF會與自訂篩選器和規則搭配使用，以協助管理DDOS攻擊。

* **分散式拒絕服務** (DDoS)是一種攻擊方法，可強制執行網站的伺服器以錯誤的要求來使用，且容量足以讓伺服器無法再回應合法的要求。

## 接下來呢？

這些主題並沒有任何特殊順序或順序。 這些簡報旨在向DevOps工程師、商務架構師，以及參與此重要決定(主辦Adobe Commerce的位置和方式)的任何人提供談話要點。

{{$include /help/_includes/hosting-related-links.md}}
