---
title: 產品選項設定最佳實務
description: 透過限制產品選項的數量來最佳化Adobe Commerce效能。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 產品選項最佳實務

為獲得最佳效能，每個產品最多可設定100個產品選項。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 減少產品選項

為獲得最佳網站效能，請使用以下策略來減少產品選項的數量：

- 設定複雜產品和自訂選項，作為產品變異的來源。
- 使用屬性集來建置具有目標屬性和選項的特定產品範本，而不是建立套用至所有產品的全域產品範本和選項容器。
- 透過外部產品管理系統(PMS)管理產品資訊。

## 對效能的潛在影響

設定許多產品選項會增加所有讀取和寫入作業中每個產品擷取的資料量，進而產生：

- 增加SQL查詢流量和負載 `JOIN` 作業會增加資料庫輸送量。
- 增加Adobe Commerce索引和全文檢索搜尋索引的大小。

以上列出的增加可能會以下列方式影響網站效能：

- 與屬性中包含許多選項的產品相關的大多數店面情境的回應時間更長。
- 在「管理員」中完成「產品」管理作業所需的時間大幅增加，這可能會導致逾時，尤其是與屬性清單和樹狀結構擷取（包括促銷規則管理）相關的案例。
- 可以封鎖完成非同步大量作業的大量動作，例如匯入和匯出，以及將自訂價格指派給共用目錄中的多個產品。

## 其他資訊

- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [產品屬性設定的最佳實務](product-attributes-and-options.md)
- [大量動作記錄](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [存貨整批作業API](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [培訓：使用Adobe Commerce管理目錄和產品](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
