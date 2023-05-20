---
title: 效能最佳化Recommendations
description: 依照下列建議最佳化Adobe Commerce實作的效能。
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
source-git-commit: 821ef18c1b0f00a6b9574be968ad76f0c230335c
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# 效能最佳化審查

即使效能最佳化可能來自許多方面，但有些一般性建議還是需要考量大多數情境下。 這包括基礎架構元素的設定最佳化、Adobe Commerce後端設定，以及架構擴充性規劃。

## 基礎架構

以下各節說明基礎架構最佳化的建議。

### DNS查閱

DNS查詢是尋找網域名稱所屬的IP位址的程式。 瀏覽器必須等到DNS查閱完成，才能下載每個請求的任何內容。 減少DNS查詢對於改善整體頁面載入時間非常重要。

### 內容傳遞網路(CDN)

使用CDN最佳化資產下載效能。 Adobe Commerce使用Fastly。 如果有內部部署的Adobe Commerce實作，您也應該考慮新增CDN層。

### Web延遲

資料中心的位置會影響前端使用者的網頁延遲。

### 網路頻寬

充足的網路頻寬是網路節點、資料庫、快取/工作階段伺服器和其他服務之間資料交換的主要需求之一。

由於Adobe Commerce有效利用快取以獲得高效能，因此您的系統可主動與Redis等快取伺服器交換資料。 如果Redis位於遠端伺服器上，您必須在Web節點和快取伺服器之間提供足夠的網路通道，以防止讀取/寫入作業出現瓶頸。

### 作業系統（作業系統）

與其他高負載Web應用程式相比，Adobe Commerce的作業系統設定和最佳化類似。 隨著伺服器處理的同時連線數目增加，可用的通訊端數目可以完全配置。

### Web節點的CPU

一個CPU核心可以有效地處理大約2-4個Adobe Commerce請求，而不需要快取。 若要確定需要多少個Web節點/核心來處理所有傳入的請求，而不將其放入佇列中，請使用下列方程式：

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### PHP-FPM設定

最佳化這些設定取決於不同專案的效能測試結果。

- **ByteCode** — 若要在PHP 7上從Adobe Commerce中獲得最大速度，您必須啟動 `opcache` 模組，並正確設定。

- **APCU** — 我們建議啟用PHP APCu擴充功能並設定Composer，以最佳化效能。 此擴充功能可快取已開啟檔案的檔案位置，進而提高Adobe Commerce伺服器呼叫（包括頁面、Ajax呼叫和端點）的效能。

- **Realpath_cacheconfiguration** — 正在最佳化 `realpath_cache` 可讓PHP處理序快取檔案的路徑，而不是在每次頁面載入時查詢它們。

### 網頁伺服器

使用nginx做為網頁伺服器只需要稍作重新配置。 nginx網頁伺服器提供更優異的效能，並可使用Adobe Commerce的範例設定檔案輕鬆設定([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample))。

- 使用TCP正確設定PHP-FPM

- 啟用HTTP/2和Gzip

- 最佳化工作者連線

### 資料庫

本檔案未提供深入的MySQL調整指示，因為每個存放區和環境都不同，但我們可以提出一些一般建議。

Adobe Commerce資料庫（以及任何其他資料庫）對可用於儲存資料和索引的記憶體量很敏感。 為了有效運用MySQL資料索引，可用的記憶體量至少應接近資料庫中儲存資料大小的一半。

最佳化 `innodb_buffer_pool_instances` 設定，以避免多個執行緒嘗試存取相同執行個體時發生問題。 的值 `max_connections` 引數應該與應用程式伺服器中設定的PHP執行緒總數相關。 使用下列公式計算的最佳值 `innodb-thread-concurrency`：

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### 工作階段快取

工作階段快取是為Redis的個別執行個體設定的良好候選項。 此快取型別的記憶體設定應考慮網站的購物車放棄策略，以及工作階段預計會在快取中保留多長時間。

Redis應配置足夠的記憶體，以保留記憶體中的所有其他快取，以獲得最佳效能。 區塊快取將是決定要設定的記憶體數量的關鍵因素。 區塊快取會隨著網站上頁數的增加而成長（SKU數量x商店檢視次數）。

### 頁面快取

強烈建議您在您的Adobe Commerce商店中使用Varnish來取得完整頁面快取。 此 `PageCache` 模組仍存在於程式碼基底中，但應僅用於開發目的。

將Varnish安裝在Web層前面的獨立伺服器上。 它應接受所有傳入請求並提供快取頁面副本。 為了讓Varnish有效地處理安全頁面，可以將SSL終止Proxy放置在Varnish之前。 Nginx可用於此用途。

雖然Varnish全頁快取記憶體失效有效，我們建議為Varnish分配足夠的記憶體，以便在記憶體中儲存您最常用的分頁。

### 訊息佇列

Message Queue Framework (MQF)是一種允許模組將訊息發佈到佇列的系統。 它也會定義非同步接收訊息的消費者。 Adobe Commerce支援 [!DNL RabbitMQ] 作為傳訊代理人，提供可擴充的平台以傳送及接收訊息。

### 效能測試和監控

我們一律建議您在每個生產版本之前進行效能測試，以取得電子商務平台功能的預估值。 啟動後持續監控，並針對處理尖峰時間制定擴充性與備份計畫。

>[!NOTE]
>
> 雲端基礎結構上的Adobe Commerce已套用上述所有的基礎結構和架構最佳化，但DNS查詢除外，因為它不在範圍內。

### 搜尋 {#search-heading}

自Adobe Commerce 2.4版開始，需要Elasticsearch （或OpenSearch），但最佳實務是為2.4版之前的版本啟用。

## 作業模型

除了前述的一般基礎架構最佳化建議外，還有可針對特定業務模式和規模提升效能的方法。 本檔案並未針對所有案例提供深入調整指示，因為每個案例都不同，但我們可以提供一些高階選項供您參考。

### Headless架構

我們有一個單獨的區段專門用於詳細說明以下內容 [headless](../../architecture/headless/adobe-commerce.md) 和不同的選項。 總而言之，它將店面圖層與平台本身分開。 這仍是相同的後端，但Adobe Commerce不再直接處理請求，而是僅透過GraphQL API支援自訂店面。

### 保持Adobe Commerce更新

執行最新版本時，Adobe Commerce一律會有較佳的效能。 即使在每個新版本發行後無法保持Adobe Commerce最新狀態，仍建議使用 [升級](../../../upgrade/overview.md) Adobe Commerce推出重大效能最佳化時。

例如，在2020年，Adobe發佈了Redis層的最佳化，修正了許多低效率、連線問題，以及Redis和Adobe Commerce之間不必要的資料傳輸。 整體效能介於2.3和2.4之間，是白天和黑夜，我們發現購物車、結帳、同時使用者等專案都由於Redis最佳化而獲得重大改善。

### 最佳化資料模型

許多問題源自資料，包括錯誤的資料模型、未正確建構的資料以及遺漏索引的資料。

如果您正在測試一些連線，看起來會不錯，但在生產環境中會看到實際流量點選，而且這會造成速度變慢。 系統整合經銷商瞭解如何設計資料模型（尤其是產品屬性）、避免新增不必要的屬性，以及保留影響商業邏輯的強制屬性（例如定價、庫存供應和搜尋）非常重要。

對於不會影響商業邏輯但仍需要顯示在店面上的屬性，請將它們合併為幾個屬性（例如JSON格式）。

為了最佳化平台效能，如果店面不需要商業邏輯（來自於從PIM或ERP取得的資料或屬性），則不需要將該屬性新增到Adobe Commerce。

### 針對擴充性而設計

這對於經常執行行銷活動並面對高峰期的企業來說很重要。 架構和應用程式設計易於擴展，因此可在尖峰時段增加資源，並在尖峰時段後減少資源。
