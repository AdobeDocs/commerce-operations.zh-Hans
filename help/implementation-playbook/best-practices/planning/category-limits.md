---
title: 類別設定最佳實務
description: 瞭解最佳實務，以透過限制目錄中的類別數量來最大化網站效能。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: c6834b32-9ee8-4a4a-932c-9726f3feee3f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 類別設定的最佳實務

為獲得最佳效能，請勿為Adobe Commerce網站設定超過建議的最大類別數量。

- 若是Adobe Commerce 2.4.2版或更新版本，最多可設定6000個類別
- 若為Adobe Commerce 2.3.x版和2.4.0至2.4.1-p1，請設定最多3000個類別

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 減少產品數量

使用下列策略來減少類別數量：

- 透過屬性和自訂選項管理獨特的產品功能
- 移除非使用中類別
- 最佳化導覽中的目錄深度

## 對效能的潛在影響

擁有超過建議的最大類別數可能會透過下列方式影響網站效能：

- 非快取目錄頁面的回應時間明顯增加
- 從管理員管理類別時的長時間執行和逾時
- 增加對應資料庫表格的大小
- 較大的索引表格會增加完成索引操作所需的時間 `[category/product relation index\]`
- 增加處理時間，以完成類別樹狀結構建立、功能表擷取和類別規則管理作業

## 其他資訊

- [類別概觀](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [導覽概述](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [產品指派](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [雲端基礎結構上的Adobe Commerce：商店設定的最佳實務](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
