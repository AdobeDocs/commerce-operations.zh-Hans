---
title: 效能標竿
description: 檢閱在Adobe雲端基礎結構上託管的Adobe Commerce實施的效能基準結果。
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: eeb7146a8051e8692ebf974d65db75a4999cf2e6
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# 基準摘要

Adobe Commerce 2.4.5效能基準結果反映了在部署有下列基礎架構和其他元件的Adobe Commerce執行個體上測量到的效能。
- [Pro雲端環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) 替換為 [縮放架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [Adobe Commerce的B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

沒有其他自訂專案。

下列資訊會概述效能標竿結果，並提供測試期間使用的環境和資料相關資訊。

## 關鍵效能量度

下圖顯示效能基準的Commerce存放區設定，以及測試結果的關鍵效能量度。

![效能標竿JMeter和生產基礎結構](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

根據模擬企業B2C組織的測試條件，系統可以在標準負載流程中處理尖峰期間請求的流量和訂單數量。

### 效能亮點

- **訂購** — 每分鐘處理3,481筆訂單，而第99個百分位數的回應時間維持在2秒以內（99%的請求獲得服務且回應時間少於2秒）。
- **頁面檢視** — 每小時處理超過200萬次頁面檢視，同時將第99個百分位數的回應時間維持在2秒以內。
- **有效SKU** — 客戶設定檔包含2.42億種不同的價格變化(<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKUs</a>)適用於250,000種產品。
- **GraphQL請求** — 系統擴充至每分鐘10,500個GraphQL未快取要求，同時在第99個百分位數維持不到2秒的回應時間。
- **同時管理員使用者** — 系統可擴充至支援500名同時管理使用者，同時在第99個百分位數維持不到2秒的回應時間。

## 測試環境

效能基準測試結果是透過針對部署在具有縮放架構的Pro雲端環境中的Adobe Commerce 2.4.5執行個體進行測試而獲得的。 執行個體也已安裝、設定和啟用Adobe Commerce B2B、Inventory management和Adobe Stock整合模組。

測試設定檔的效能測試資料是使用 <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Performance Toolkit</a>.

效能評量以客戶和商務使用者的模擬日常商店活動為基礎。 值反映每個案例的接近最大輸送量，但並不反映獨特的業務模式，例如私人銷售或瞬間銷售。

- **LUMA店面**
   - 店面同時有3000位使用者
   - 設定為30% CDN快取命中率

      有效使用快取層會增加每小時的頁面檢視次數。

- **GRAPHQL API**
   - 250個並行執行緒
   - 設定為0% CDN快取命中率

      透過GraphQL前方的快取層，可大幅改善回應時間。

- **管理網頁**
   - 500位同時使用者
   - 設定為0% CDN快取命中率

## 測試環境規格

載入測試已使用針對Adobe Commerce執行個體執行的JMeter載入設定檔完成。 測試期間使用了三個Web節點和三個服務節點。 以下影像詳細說明JMeter和生產基礎結構的進入點。

![效能標竿JMeter和生產基礎結構](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### 應用

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> 部署在雲端基礎結構上，並採用Pro架構。

### 基礎架構

就效能基準而言，Adobe Commerce 2.4.5部署於 [可擴充的基礎架構](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) 具有下列容量。

- **Web節點規格**
   - vCPU 216 （72 x 3個節點）
   - 記憶體432 GiB （144 x 3節點）
   - 網路頻寬768 Gbps （256 x 3節點）
   - EBS頻寬57000 Mbps (19000 x 3個節點)
   - 布建的儲存空間100 GB

- **服務節點規格**
   - vCPU 192 （64 x 3個節點）
   - 記憶體768 GiB （256 x 3節點）
   - 網路頻寬60 Gbps （20 x 3個節點）
   - EBS頻寬40800 Mbps (13600 x 3個節點)
   - 布建的儲存空間1100 GB
