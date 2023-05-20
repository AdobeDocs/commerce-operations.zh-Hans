---
title: 產品變數設定最佳實務
description: 瞭解如何透過限制已設定的產品變數數目來最佳化Adobe Commerce效能。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: a19dd8b4-23b8-498f-be51-a0adfcd12a11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# 設定產品變數的最佳實務

為獲得最佳效能，請為每個產品設定最多50個變數。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 減少產品變數數量

為獲得最佳網站效能，請使用以下策略來減少產品變異數：

- 透過分佈不同產品的變異數來重新建構目錄。
- 移除沒有庫存的可設定屬性選項。
- 透過自訂選項、類別、相關、分組和套裝產品等替代功能管理變體。

## 對效能的潛在影響

超過建議的產品變數數目可能會透過下列方式影響網站效能：

- 產品詳細資料和包含複雜產品的類別頁面上的長請求和呈現時間。
- 增加在管理員中完成儲存作業的回應時間。
- 增加呈現產品編輯表單的時間。
- 結帳緩慢。

## 其他資訊

- [建立可設定的產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- 訓練 — [使用Adobe Commerce管理目錄和產品](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
