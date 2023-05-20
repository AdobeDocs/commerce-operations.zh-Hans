---
title: 私人內容區塊的最佳實務
description: 瞭解設定私人內容區塊的最佳實務，以最佳化店面效能。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# 私人內容區塊的最佳實務

當私人內容區塊包含 `_isScopePrivate` 變數，無法快取區塊。 由於未快取私密區塊，因此Adobe Commerce必須為每個客戶請求擷取相同的資料，這會增加伺服器負載。

不要使用 `_isScopePrivate` 變數，建立區塊和範本以顯示與使用者無關的資料。 此資料會由Adobe Commerce UI元件取代為使用者專屬的資料，此元件可更有效率地處理預先呈現的資料。 如需指示，請參閱 [私人內容](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) 在 _[!DNL Commerce PHP Extensions Guide]_.

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 對效能的潛在影響

具有私人內容區塊的網站，包含 `_isScopePrivate` 變數會觸發AJAX請求，以擷取每個客戶請求的相同資料。 這會增加回應時間，並使用可用於處理更多關鍵業務店面作業的其他資源，例如客戶註冊、購物車更新、訂單提交和付款交易。

## 其他資訊

- [私人內容](../../../performance/configuration.md#client-side-optimization-settings)
- [高輸送量AJAX要求導致效能不佳](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
