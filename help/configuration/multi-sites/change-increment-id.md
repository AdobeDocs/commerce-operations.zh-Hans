---
title: 變更增量ID
description: 變更Commerce資料庫實體的增量ID。
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# 變更增量ID

本文討論如何使用變更特定Commerce商店中Commerce資料庫(DB)實體（訂單、發票、銷退折讓單等）的增量ID。 `ALTER TABLE` SQL陳述式。

## 受影響的版本

- Adobe Commerce （內部部署）： 2.x.x
- 雲端基礎結構上的Adobe Commerce： 2.x.x
- MySQL： [任何支援的版本](../../installation/prerequisites/database/mysql.md)

## 您何時需要變更增量ID

在下列情況下，您可能需要變更新DB實體的增量ID：

- 在即時網站上執行硬式備份還原之後
- 有些訂單記錄已遺失，但付款閘道（例如PayPal）已使用其ID代管您目前的商家帳戶。 在這種情況下，付款閘道會停止處理具有相同ID的新訂單，傳回「重複的商業發票ID」錯誤

>[!INFO]
>
>您也可以在PayPal的「付款接收偏好設定」中，允許每個商業發票ID具有多個付款，以修正PayPal的付款閘道問題。 另請參閱 [PayPal閘道已拒絕請求 — 重複發票問題] 在 _知識庫_.

## 必要條件步驟

1. 尋找應變更新增量ID的存放區和實體。
1. 連線至您的MySQL資料庫。
針對雲端基礎結構上的Adobe Commerce，您首先需要使用SSH連線至您的環境。
1. 檢查目前的 `auto_increment` 使用下列查詢的實體序清單格值：

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

如果您要檢查ID=1之存放區中訂單的自動增量，表格名稱將是&#39;sequence_order_1&#39;。

如果 `auto_increment` 欄為&#39;1234&#39;，即為下個在商店下單的訂單，帶有 `ID=1` 將具有ID &#39;#100001234&#39;。

## 更新實體以變更增量ID

使用下列查詢更新實體：

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
重要：新增量值必須大於目前值。

執行以下查詢之後：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

在商店下個訂單，使用 `ID=1` 將具有ID &#39;#100002000&#39;。

## 雲端生產環境的其他建議步驟

執行之前 `ALTER TABLE` 在雲端基礎結構上的Adobe Commerce生產環境中進行查詢，我們強烈建議您執行下列步驟：

- 在中繼環境中測試變更增量ID的整個程式
- [建立資料庫備份] 以在失敗時還原您的生產DB

<!-- Link Definitions -->

[PayPal閘道已拒絕請求 — 重複發票問題]: https://support.magento.com/hc/en-us/articles/115002457473
[建立資料庫備份]: https://support.magento.com/hc/en-us/articles/360003254334
[任何支援的版本]
