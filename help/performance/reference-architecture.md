---
title: 參考架構
description: 檢閱Adobe Commerce和Magento Open Source部署的建議參考架構圖表。
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# 參考架構

本主題說明一般建議設定，適用於Adobe Commerce和Magento Open Source執行個體，使用實體託管於資料中心（非虛擬化）的普通伺服器，資源不會與其他使用者共用。 您的託管提供者（尤其是專長於Commerce高效能託管的提供者）可能會建議採取對您的需求相同或更有效率的不同設定。

如需雲端基礎結構環境上的Adobe Commerce，請參閱 [入門架構](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] 參考架構圖

此 [!DNL Commerce] 參考架構圖表代表設定可擴充架構的最佳作法 [!DNL Commerce] 網站。

圖表中每個元素的顏色會指出該元素是否為Magento Open Source或Adobe Commerce的一部分，以及是否需要。

* Magento Open Source需要橘色元素
* 灰色元素是Magento Open Source的選用元素
* 藍色元素是Adobe Commerce的選用元素

![Commerce參考架構圖](../assets/performance/images/ref-architecture-2.3.png)

以下章節提供Commerce參考架構圖表中每個區段的建議和考量事項。

### [!DNL Varnish]

* A [!DNL Varnish] 叢集可擴充至網站的流量
* 根據所需的快取頁數調整執行處理大小
* 在高流量的網站上，使用 [!DNL Varnish] Master可確保快取上排清每個網頁層級一個請求（最多）

### Web

* 啟用節點規模以提供流量和備援
* 一個節點為主節點並執行cron
* 或者，使用專屬的管理員和工作者節點

### 快取

* 請考慮為工作階段實作個別的Redis例項
* 您可以為每個快取有一個Redis執行個體
* 調整執行個體大小，使其包含預期的最大快取大小

### 資料庫和佇列

* 高流量的網站可以使用從屬資料庫調整資料庫效能，並針對訂單/購物車分割資料庫(在Adobe Commerce中)
* 請考慮使用從屬資料庫來啟用快速復原及資料備份
* 低流量網站可以將影像儲存在DB中

### 搜尋 {#search-heading}

* 根據搜尋流量調整執行個體數量

### 儲存

* 請考慮使用GFS或GlusterFS來儲存pub/media
* 或者，將DB儲存空間用於低流量的網站

### 建議 [!DNL Varnish] 參考架構

Magento支援數個完整頁面快取引擎(檔案、Memcache、Redis、 [!DNL Varnish])立即可用，並透過擴充功能擴大涵蓋範圍。 [!DNL Varnish] 是建議的完整頁面快取引擎。  [!DNL Commerce] 支援許多不同的功能 [!DNL Varnish] 設定。

針對不需要高可用性的網站，我們建議使用簡單的 [!DNL Varnish] 設定Nginx SSL終止。

![簡單 [!DNL Varnish] 使用SSL終止進行設定](../assets/performance/images/single-varnish-with-ssl-termination.png)

對於需要高可用性的網站，我們建議使用2層級 [!DNL Varnish] 使用SSL終止負載平衡器的設定。

![高可用性雙階層 [!DNL Varnish] 使用SSL終止負載平衡器的設定](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
