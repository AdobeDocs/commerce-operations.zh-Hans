---
title: Adobe Commerce效能最佳化
description: 透過變更某些預設設定，準備您的Adobe Commerce專案以使用Adobe Experience Manager as a CMS。
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
source-git-commit: a11f3ef0519a4a6c08ea1d4e520ce0462e88885d
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Adobe Commerce效能最佳化

## AEM和Adobe Commerce基礎架構的地理位置

為了減少AEM發佈者與Adobe Commerce GraphQL在建立頁面時的延遲，應該在相同的AWS （或Azure）區域內託管這兩個獨立基礎結構的初始布建。 為這兩個雲端選擇的地理位置也應該最靠近大多數客戶群，這樣使用者端GraphQL請求就會從地理位置鄰近的位置提供給大多數客戶。

## Adobe Commerce中的GraphQL快取

當使用者的瀏覽器或AEM發佈者呼叫Adobe Commerce的GraphQL時，某些呼叫將會在Fastly中快取。 快取的查詢通常是包含非個人資料且不太可能經常變更的查詢。 例如：categories、categoryList和products。 明確未快取的就是定期變更且若快取，可能會對個人資料和網站作業（例如購物車和customerPaymentTokens等查詢）帶來風險的查詢。

GraphQL可讓您在單一呼叫中進行多個查詢。 請務必注意，如果您指定甚至Adobe Commerce未快取的一個查詢，以及許多無法快取的其他查詢，Adobe Commerce將略過呼叫中所有查詢的快取。 開發人員在合併多個查詢時應該考慮這一點，以確保潛在的可快取查詢不會被無意中繞過‡。

>[!NOTE]
>
> 如需可快取和不可快取查詢的詳細資訊，請參閱Adobe Commerce [開發人員檔案](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## 目錄平面表格

不建議對產品和類別使用平面表格。 使用此已棄用的功能可能會導致效能降低和索引問題，因此應透過Adobe Commerce管理員在店面區段中停用平面目錄。 某些協力廠商模組與自訂功能確實需要平面表格才能正常運作，建議進行評估以瞭解當選擇使用這些擴充功能或自訂功能時，必須使用平面表格的相關影響與風險。

## Fastly來源遮蔽

預設不會啟用Fastly來源遮蔽。 Fastly來源遮蔽的目的是減少直接到Adobe Commerce來源的流量：當收到請求時，Fastly邊緣位置（或「存在點」/POP）會檢查快取內容並提供它。 如果未快取，則會繼續前往Shield POP檢查是否已快取（如果先前已請求其他全域POP的內容，則會快取）。 最後，如果未在Shield POP上快取，則只會繼續前往原始伺服器。

可以在您的Adobe Commerce管理員Fastly設定後端設定中啟用Fastly來源遮蔽。 您應選擇最接近Adobe Commerce原始資料中心的遮蔽位置，以獲得最佳效能。

## Fastly影像最佳化

啟用Fastly來源遮蔽後，這可讓您同時啟用Fastly Image Optimizer。 產品目錄影像儲存在Adobe Commerce上，此服務可讓您將所有資源密集的產品目錄影像轉換處理解除安裝到Fastly，並從Adobe Commerce來源移除。 一般使用者的回應時間也會因頁面載入時間而改善，因為在邊緣位置會轉換影像，減少傳回Adobe Commerce原點的請求數量，進而消除延遲。

Fastly影像最佳化可以透過Admin中Fastly設定的「啟用深層影像最佳化」來啟用，但前提是您的來源盾牌已啟用。 有關Fastly影像最佳化設定的更多詳細資訊，請參閱Adobe Commerce [開發人員檔案](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html).

![Adobe Commerce管理員中Fastly影像最佳化設定的熒幕擷圖](../assets/commerce-at-scale/image-optimization.svg)

## 停用未使用的模組

如果執行Adobe Commerce Headless，則只會透過GraphQL端點服務請求，而不會直接從Adobe Commerce提供前端商店頁面，因此許多模組會變得多餘且無法使用。 透過停用未使用的模組，您的Adobe Commerce程式碼庫會變得更小、更不複雜，因此可以提供效能改善。 可使用Composer管理Adobe Commerce上的停用模組。 哪些模組可以停用，取決於您網站的需求，因此不會提供建議清單，因為這會特定於每個客戶的Adobe Commerce實施。

## MySQL和Redis連線啟用

依預設，雲端上的Adobe Commerce中不會啟用MySQL和Redis從屬連線。 這是因為這些設定僅適用於預期非常高負載的客戶。 啟用從屬連線時，跨可用區（跨可用區）延遲會較高，因此在執行個體僅接收正常負載等級的情況下，此設定實際上會降低雲端執行個體上Adobe Commerce的效能。

如果Adobe Commerce執行個體預期負載極大，則啟用MySQL和Redis的主從節點會將負載分散到MySQL資料庫或Redis上，以協助提高效能。

作為指南，在負載正常的環境中，啟用從屬連線會使效能降低10-15%。 但在負載和流量較大的叢集上，效能可提升約10-15%。 因此，使用預期的流量層級負載測試您的環境非常重要，以評估此設定是否對負載下的效能時間有益。

若要啟用/停用mysql和redis的從屬連線，您應該編輯 `.magento.env.yaml` 檔案包含以下專案：

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

對於縮放架構（分割架構 — 請參閱下文），不應啟用Redis從屬連線，因為這會造成錯誤。 若是分割架構，建議改為實作Redis的L2快取。

## 在雲端縮放（分割）架構上移至Adobe Commerce

如果在完成上述所有設定後，負載測試結果或即時基礎架構效能分析仍顯示Adobe Commerce的負載等級持續充滿CPU和其他系統資源，則應考慮遷移到縮放（拆分）架構。

在標準Pro架構中，有3個節點，每個節點都包含完整的技術棧疊。 透過轉換為分割層架構，這會改變為至少6個節點：其中3個包含Elasticsearch、MariaDB、Redis和其他核心服務；其他3個用於處理網頁流量的節點包含phpfpm和NGINX。 分割層級有更大的擴充可能性：包含資料庫的核心節點可以垂直縮放；網頁節點可以水平與垂直縮放，提供大量彈性，在設定的高負載活動期間以及需要額外資源的節點上，依需求擴充基礎架構。

如果由於您的網站負載期望過高，而決定切換至分割層架構，則應與您的Adobe客戶團隊討論啟用此功能的步驟。
