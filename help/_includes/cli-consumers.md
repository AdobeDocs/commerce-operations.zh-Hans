---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# 訊息佇列消費者的CLI選項

| 名稱 | 說明 | 值 | 必填 |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | 決定消費者是否將等待來自佇列的訊息。 | 1 — 是，0 — 否 | 否 |

* `0`：消費者處理佇列中的可用訊息、關閉TCP連線並終止。 即使已處理的訊息數量少於 `--max_messages` 在啟動消費者期間指定的值。

* `1`：消費者會繼續處理來自訊息佇列的訊息，直到達到訊息數量上限（為指定的值）。 `--max_messages` 於 `queue:consumers:start` 命令)，然後關閉TCP連線並終止取用者處理序。 如果佇列在到達之前是空的 `--max_messages` 消費者會等待更多訊息到達。 如果您使用背景工作來執行消費者，而不是使用cron工作，請將此變數設為 `1`.

>[!WARNING]
>
>此 `--consumers-wait-for-messages` 選項為全域選項，無法個別為每個消費者設定。
