---
title: 訂單處理的設定最佳實務
description: 瞭解設定最佳實務，以改善結帳和訂單處理效能。
role: Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# 訂單處理的設定最佳實務

隨著您的Commerce網站上訂購量的增加，您可以啟用以下商店設定選項，以最佳化結帳效能和訂單處理：

- **[!UICONTROL Asynchronous indexing]** — 啟用此選項可防止同時下大量訂單時資料庫鎖定並減緩處理速度。
- **[!UICONTROL Asynchronous email notifications]** — 啟用此選項可透過按指定間隔傳送結帳和訂單處理電子郵件通知（而不是立即傳送）來加速結帳效能。
- **[!UICONTROL Enable Archiving]** — 啟用此選項可改善訂單、商業發票、出貨及銷退折讓單的效能，並且讓您的工作區沒有不必要的資訊，讓您能夠專心處理目前的業務。 另請參閱 [啟用封存](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 啟用非同步訂單處理

啟用非同步訂單處理的步驟取決於部署模式：

- 對於雲端基礎結構上的Adobe Commerce和生產模式下的內部部署網站，請使用以下MagentoCLI命令來啟用非同步索引：

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- 對於處於預設或生產模式的Adobe Commerce內部部署網站，請透過更新「管理員」中的「網格設定」設定來啟用非同步索引。

   另請參閱 [啟用排定的網格更新並重新索引](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >在更新生產環境之前，請一律在中繼環境中測試設定變更。

## 其他資訊

- [設定最佳實務](../../../performance/configuration.md)
- [一般和進階設定路徑參考](../../../configuration/reference/config-reference-general.md)
- [高輸送量訂單處理](../../../performance/high-throughput-order-processing.md)
