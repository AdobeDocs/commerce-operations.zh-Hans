---
title: 產品清單分頁的最佳實務
description: 瞭解如何透過管理店面目錄每個頁面上顯示的產品數量來最佳化Adobe Commerce效能。
role: User, Admin
feature: Best Practices
feature-set: Commerce
exl-id: 473f23a9-53fb-41a6-9b3a-af7bd1208be0
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 產品清單分頁的最佳實務

為獲得最佳效能，每頁最多可顯示48種產品。

您可以設定Adobe Commerce，讓購物者可以在單一頁面上檢視所有類別產品。 如果類別產品的數量大幅超過48種產品，請更新店面分頁控制的類別目錄設定。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 更新產品清單設定

如果您在任何類別中有超過48種產品，請更新店面目錄設定以停用選項 **允許每頁所有產品**.

停用此選項後，Adobe Commerce會使用列出店面分頁控制項的產品清單，來管理顯示在店面元件中的產品數量。 如需指示，請參閱 [設定分頁控制項](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## 其他資訊

- [設定產品清單](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
