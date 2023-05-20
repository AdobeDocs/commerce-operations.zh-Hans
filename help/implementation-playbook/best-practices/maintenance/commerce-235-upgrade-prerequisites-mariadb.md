---
title: MariaDB的Adobe Commerce 2.3.5升級先決條件
description: 瞭解如何準備Adobe Commerce資料庫，以從Adobe Commerce 2.3.5升級。
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---

# 升級MariaDB的必要條件

從Adobe Commerce 2.3.4或更早版本升級至任何更新版本，需要雲端基礎結構上的MariaDB服務從10.0或10.2版升級至10.3或10.4版。MariaDB 10.3版及更新版本要求資料庫使用動態表格列格式，而Adobe Commerce要求使用InnoDB表格儲存引擎。 本文說明如何更新資料庫以符合這些MariaDB要求。

準備資料庫後，請先提交Adobe Commerce支援票證以更新雲端基礎結構上的MariaDB服務版本，然後再繼續進行Adobe Commerce升級程式。

## 受影響的產品和版本

使用Adobe Commerce 2.3.4版或更早版本以及MariaDB 10.0版或更早版本在雲端基礎結構上使用Adobe Commerce。

## 準備資料庫以進行升級

在Adobe Commerce支援團隊開始升級程式之前，請先轉換資料庫表格以準備資料庫：

- 轉換資料列格式 `COMPACT` 至 `DYNAMIC`
- 變更儲存引擎 `MyISAM` 至 `InnoDB`

在計畫和排程轉換時，請謹記下列考量事項：

- 轉換自 `COMPACT` 至 `DYNAMIC` 使用大型資料庫可能需要數小時的資料表。

- 為避免資料損毀，請勿在已上線的網站上完成轉換工作。

- 在網站上的低流量期間完成轉換工作。

- 切換您的網站至 [維護模式](../../../installation/tutorials/maintenance-mode.md) 執行命令以轉換資料庫表格之前。

### 轉換資料庫表格列格式

您可以在叢集中的單一節點上轉換表格。 變更會自動復寫到其他服務節點。

1. 在雲端基礎結構環境中，從您的Adobe Commerce使用SSH連線到節點1。

1. 登入MariaDB。

1. 識別要從壓縮格式轉換為動態格式的表格。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 決定表格大小，以便排程轉換工作。

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   較大的表格需要較長時間才能轉換。 檢閱表格並按優先順序和表格大小批次化轉換工作，以協助規劃所需的維護視窗。

1. 將所有表格一次轉換一個動態格式。

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

### 轉換資料庫表格儲存體格式

您可以在叢集中的單一節點上轉換表格。 變更會自動復寫到其他服務節點。

Adobe Commerce Starter和Adobe Commerce Pro專案的儲存格式轉換程式不同。

- 對於入門架構，請使用MySQL `ALTER` 命令轉換格式。
- 在Pro架構上，使用MySQL `CREATE` 和 `SELECT` 用來建立資料庫表格的命令 `InnoDB` 儲存並將現有表格的資料複製到新表格中。 此方法可確保將變更復寫到叢集中的所有節點。

**轉換Adobe Commerce Pro專案的表格儲存格式**

1. 識別使用的表格 `MyISAM` 儲存。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 將所有表格轉換為 `InnoDB` 一次一個儲存格式。

   - 重新命名現有表格以避免名稱衝突。

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - 建立使用的表格 `InnoDB` 使用現有表格中的資料進行儲存。

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - 確認新表格具有所有必要資料。

   - 刪除您重新命名的原始表格。


**轉換Adobe Commerce Starter專案的表格儲存格式**

1. 識別使用的表格 `MyISAM` 儲存。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 轉換使用的表格 `MyISAM` 儲存至 `InnoDB` 儲存。

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### 驗證資料庫轉換

在排程升級至MariaDB 10.2版的前一天，請確認所有表格都具有正確的列格式和儲存引擎。 需要進行驗證，因為完成轉換後進行的程式碼部署可能會導致某些表格恢復為原始設定。

1. 登入您的資料庫。

1. 檢查是否有任何表格仍具有 `COMPACT` 列格式。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 檢查是否有任何表格仍使用 `MyISAM` 儲存格式

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 如果有任何表格已還原，請重複變更表格列格式和儲存引擎的步驟。

## 變更儲存引擎

另請參閱 [將MyISAM表格轉換為InnoDB](../planning/database-on-cloud.md).

## 其他資訊

- [雲端基礎結構上Adobe Commerce的資料庫最佳實務](../planning/database-on-cloud.md)
- [針對Adobe Commerce on Cloud將MariaDB從10.0更新至12.0](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10.0-to-10.2-for-magento-commerce-cloud.html)
