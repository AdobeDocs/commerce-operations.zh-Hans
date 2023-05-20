---
title: 設定促銷活動的最佳作法
description: 瞭解設定銷售規則和優惠券代碼的最佳實務，以最佳化Commerce商店效能。
role: User
feature: Best Practices
feature-set: Commerce
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 設定促銷活動的最佳作法

為獲得最佳效能，請遵循下列最佳實務，為購物車中的商品設定銷售和促銷活動：

- **銷售規則（購物車價格規則）** — 為所有網站設定不超過1000個購物車價格規則
   - 管理和移除未使用的規則。
   - 新增嚴格的規則條件（如屬性或類別篩選）以獲得最有效的比對。
- **優惠券**—
   - 確認資料庫中的抵用券總數少於250,000。
   - 移除未使用和過期的抵用券。
   - 僅產生符合行銷活動要求所需的抵用券數目。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 對效能的潛在影響

擁有超過建議的最大購物車價格規則或優惠券數量可能會以下列方式影響網站效能：

- 將產品新增至購物車時增加回應時間。
- 增載入入和轉譯迷你藝術的時間。
- 增加轉譯購物車頁面的時間。
- 增加呈現 **總計** 在「結帳」頁面上封鎖。
- 套用優惠券可能需要超過2秒的時間。

## 其他資訊

- [瞭解行銷活動和促銷活動](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [購物車價格規則](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [教學課程：建立購物車價格規則](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [優惠券代碼](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [雲端基礎結構上的Adobe Commerce：商店設定的最佳實務](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
