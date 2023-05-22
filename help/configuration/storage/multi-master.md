---
title: 分割資料庫效能解決方案
description: 閱讀Adobe Commerce和Magento Open Source的分割資料庫解決方案。
recommendations: noCatalog
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# 分割資料庫解決方案概觀

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce提供數個可擴充性優勢，包括能夠為Commerce應用程式的不同功能區域使用三個獨立的主資料庫。

結帳、訂購和產品資料都可以使用單獨的主資料庫，您可以選擇複製這些資料庫。 此分隔會根據您的需求，獨立調整網站結帳、訂單管理活動、網站瀏覽和銷售活動的負載。 這些變更在如何縮放資料庫層級方面提供了相當大的彈性。

>[!INFO]
>
>雲端基礎結構上的Adobe Commerce可以 _not_ 支援此功能。

此 `ResourceConnections` 類別提供與Commerce應用程式的統一MySQL資料庫連線。 針對主要資料庫的查詢，我們實作命令查詢職責劃分(CQRS)資料庫模式。 此模式會處理將讀取和寫入查詢路由到適當資料庫的邏輯。 開發人員不需要知道正在使用哪個設定，也沒有獨立的讀取和寫入資料庫連線。

如果您設定可選的資料庫復寫，則可獲得下列優點：

- 資料備份
- 在不影響master資料庫的情況下進行資料分析
- 擴充性

MySQL資料庫會以非同步方式復寫，這表示從屬端不需要永久連線即可接收主端的更新。

下圖說明此功能的運作方式。

![Adobe Commerce使用不同的資料庫來儲存表格](../../assets/configuration/split-db-diagram-ee.png)

在Magento Open Source中，僅使用一個master資料庫。

Adobe Commerce使用三個主要資料庫和可供設定的從屬資料庫數目進行復寫。 Adobe Commerce提供單一介面用於資料庫連線，因此效能更佳，而且可擴充性也更好。

## 設定選項

由於分割資料庫效能解決方案的設計方式，您的自訂程式碼和已安裝的元件 _無法_ 執行下列任一項作業：

- 直接寫入資料庫(您必須改用Adobe Commerce資料庫介面)
- 使用影響銷售或報價資料庫的JOIN
- 在結帳、銷售或主要資料庫中使用資料表的外部索引鍵

>[!WARNING]
>
>請聯絡元件開發人員，確認其元件是否執行前述任何動作。 若是如此，您只能選擇下列其中一項：
>
>- 要求元件開發人員更新其元件。
>- 按原樣使用元件 _不含_ 分割資料庫解決方案。
>- 移除元件，以便使用分割資料庫解決方案。


這也表示您可以：

- 設定分割資料庫解決方案 _早於_ 將Commerce投入生產。

   Adobe建議您在安裝Commerce軟體後，儘快設定分割資料庫。

- [手動設定](multi-master-manual.md) 分割資料庫解決方案。

   如果您已安裝元件，或Commerce已在生產環境中，則必須執行此工作。 (_不要_ 更新生產系統；在開發系統中進行更新，並在您測試變更後同步化變更。)

   >[!WARNING]
   >
   >您必須手動備份另外兩個資料庫執行處理。 Commerce只會備份主要資料庫執行個體。 此 [`magento setup:backup --db`](../../installation/tutorials/backup.md) 命令和管理選項不會備份其他表格。

## 必要條件

分割資料庫需要您在任一主機上設定三個MySQL master資料庫（三個MySQL資料庫都在Commerce伺服器上，每個資料庫都安裝在個別伺服器上，依此類推）。 這些是 _主版_ 資料庫及其使用方式如下：

- 一個用於簽出表格的主資料庫
- 一個銷售表格的主資料庫(也稱為 _訂單管理系統_，或 _OMS_，表格)
- Commerce 2應用程式表格的其餘部分有一個主資料庫

此外，您可以選擇設定任意數量的 _從屬_ 做為負載平衡器和備份的資料庫。

本指南僅討論如何設定主資料庫。 我們提供範例組態和參考，讓您視需要設定從屬資料庫。

在本指南中，將命名三個主要資料庫：

- `magento_quote`
- `magento_sales`
- `magento`

（您可以隨意命名資料庫。）
