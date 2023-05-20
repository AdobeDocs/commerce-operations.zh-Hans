---
title: MySQL觸發程式使用狀況
description: 瞭解如何透過Adobe Commerce有效使用MySQL觸發程式。
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: acac3e47-67c8-4eea-80e3-e26f2854391a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# MySQL觸發程式使用的最佳實務

本文說明在使用MySQL觸發程式時如何避免效能問題。 觸發器用於將變更記錄到稽核表中。

## 受影響的產品和版本

- Adobe Commerce內部部署
- 雲端基礎結構上的Adobe Commerce

>[!WARNING]
>
>對於雲端專案上的Adobe Commerce，在變更生產環境的設定之前，請一律在中繼環境中測試設定變更。

## 瞭解效能影響

觸發器會解譯為程式碼，表示MySQL不會預先編譯它們。

掛接到查詢的交易空間時，觸發器會為使用表格執行的每個查詢向剖析器和解譯器增加額外負荷。 觸發程式與原始查詢共用相同的交易空間，當這些查詢爭奪表格上的鎖定時，觸發程式會獨立爭奪其他表格上的鎖定。

如果使用許多觸發程式，此額外額外開銷可能會對網站上的網站效能造成負面影響。

>[!WARNING]
>
>Adobe Commerce不支援Adobe Commerce資料庫中的任何自訂觸發器，因為自訂觸發器可能會與未來Adobe Commerce版本不相容。 如需最佳實務，請參閱 [一般MySQL准則](../../../installation/prerequisites/database/mysql.md) (位於Adobe Commerce檔案中)。

## 有效使用觸發程式

若要防止使用觸發程式時發生效能問題，請遵循下列准則：

- 如果您有在執行觸發程式時寫入某些資料的自訂觸發程式，請移動此邏輯以直接寫入稽核表格。 例如，在應用程式程式碼中新增其他查詢，然後在您要為其建立觸發器的查詢後執行。
- 檢閱現有的自訂觸發程式，並考慮移除這些觸發程式，然後直接從應用程式端寫入表格。 使用檢查資料庫中現有的觸發程式 [`SHOW TRIGGERS` SQL陳述式](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- 如需其他協助、疑問或顧慮， [提交Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## 其他資訊

- [MySQL必要條件](../../../installation/prerequisites/database/mysql.md)
- [雲端基礎結構上Adobe Commerce的資料庫最佳實務](database-on-cloud.md)
