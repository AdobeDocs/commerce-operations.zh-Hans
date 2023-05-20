---
title: 產品限制最佳實務
description: 瞭解設定產品庫存單位(SKU)的最佳實務，以最大化網站效能。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 37af7b92-05ac-4a4f-9009-11e8d9f95c2f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# 產品SKU設定的最佳實務

為了最大化效能，建議的有效產品庫存單位(SKU)最大值為2.42億。 此有效產品SKU上限的計算方式為：

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

其中：

- N代表該類別的專案數
- 客戶群組包含共用目錄，因為它會建立額外的客戶群組。

有效SKU的數量超過上限，會減慢產品資料擷取的速度，並增加完成管理員面板操作或索引的時間。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 減少產品數量

使用下列策略來減少產品數量(SKU)：

- 最小化乘數 — 
   - 整合網站可減少乘數。 如果您有50,000個SKU、10個網站和10個客戶群組，SKU的有效數量為500萬。 移除五個客戶群組，將有效SKU減少至250萬。
   - 使用自訂定價的替代產品功能來取代共用目錄和客戶群組乘數。
   - 客戶群組和共用目錄兩者都是商店中有效SKU數目的乘數。
- 重新建構目錄 — 
   - 減少指派給類別的產品數量。
   - 減少網站、客戶群組、共用目錄、產品數量或可設定產品選項的數量，以減少SKU的數量
- 使用自訂選項而非建立個別產品，以提供更多產品變體。
- 考慮到有效SKU可能包含價格的多重排列，因為每個商店或客戶群組的價格可以有不同的指定。
- 停用或移除未使用的系統元件，例如模組。 (請參閱  [解除安裝模組](../../../installation/tutorials/uninstall-modules.md).)
- 在外部平台管理系統(PMS)中管理產品。

## 其他資訊

- [建立產品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [產品指派](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [使用共用目錄](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- 雲端基礎結構： [設定多個網站和商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- 內部部署： [多個網站或商店](../../../configuration/multi-sites/ms-overview.md)
- [雲端基礎結構上的Adobe Commerce：商店設定的最佳實務](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
