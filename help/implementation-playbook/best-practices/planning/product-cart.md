---
title: 產品購物車最佳實務
description: 瞭解如何透過限制購物車中的產品數量來最佳化Adobe Commerce效能。
role: User
feature: Best Practices
feature-set: Commerce
exl-id: 7ea5acc2-f6b2-4244-8c07-c71fd54a18a0
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 產品購物車管理的最佳實務

為獲得最佳效能，請使用下列准則來管理Adobe Commerce和Magento Open Source的購物車限制：

- 若為版本2.3.x - 2.4.2，購物車中最多可容納100種產品。
- 若是2.4.3版或更新版本，銷售規則功能的增強功能會將購物車數量上限增加到750個。


若為版本2.3.x - 2.4.2，根據購物車專案限制的預期效能為：

- 最多 **100** 購物車中的產品 — 產品運作正常，符合回應時間的效能目標。
- 最多 **300** 購物車中的產品 — 產品有效，但回應時間增加到超過目標。
- 以上 **500** 購物車中的產品 — 無法保證購物車和結帳流程正常運作

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 減少購物車專案數量

使用下列策略管理購物車專案數量

- 使用「 」，將訂單分割為數筆較小的訂單（列數較少）。 [!UICONTROL Add Item by SKU] 功能。
- 僅新增載入專案清單所需的自訂邏輯和購物車自訂。

## 對效能的潛在影響

購物車中產品數量超過建議的最大數量可能會透過以下方式影響網站效能：

- 增加資料擷取作業、驗證購物車專案、檢查是否套用價格規則，以及稅捐和總計計算的回應時間。
- 增加Minicart轉譯的回應時間，包括轉譯購物車檢視、結帳流程及執行。
- 增加所有出現minicart的網站頁面的載入時間。

## 其他資訊

- [設定產品選項](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [管理購物車](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
