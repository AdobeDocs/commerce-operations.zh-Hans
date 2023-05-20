---
title: 解決資料庫效能問題的最佳實務
description: 瞭解如何修正雲端基礎結構上部署的Adobe Commerce網站效能緩慢的資料庫問題。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# 解決資料庫效能問題的最佳實務

本文討論如何修正雲端基礎結構網站上Adobe Commerce上資料庫效能受到負面影響的資料庫問題。

## 受影響的版本

雲端基礎結構上的Adobe Commerce

## 識別並解決長時間執行的查詢

判斷是否有任何執行緩慢的MySQL查詢。 根據您的Adobe Commerce雲端基礎結構計畫以及相應的工具可用性，您可以執行以下操作。

### 使用MySQL分析資料庫查詢

您可以使用MySQL來識別並解決雲端基礎結構專案上任何Adobe Commerce上長時間執行的查詢。

1. 執行 [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) 陳述式。
1. 如果您發現長時間執行查詢，請執行 [MySQL `EXPLAIN` 和 `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) 逐一查詢，找出造成查詢長時間執行的因素。
1. 根據發現的問題，採取步驟修正查詢，使其更快速地執行。

### 使用Percona Toolkit分析查詢（僅適用於Pro架構）

如果您的Adobe Commerce專案部署在Pro架構上，您可以使用Percona Toolkit來分析查詢。

1. 執行 `pt-query-digest --type=slowlog` 命令（針對MySQL緩慢查詢記錄）。
   * 若要尋找緩慢查詢記錄的位置，請參閱 **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs)在開發人員檔案中。
   * 請參閱 [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) 說明檔案。
1. 根據發現的問題，採取步驟修正查詢，使其更快速地執行。

## 確認所有資料表都有主索引鍵

定義主索引鍵是良好的資料庫和表格設計的必要條件。 主索引鍵提供一種可唯一識別任何表格中單一列的方法。

如果您的表格沒有主索引鍵，Adobe Commerce (InnoDB)的預設資料庫引擎會使用第一個唯一且非null的索引鍵作為主索引鍵。 如果沒有可用的唯一金鑰，InnoDB會建立隱藏的主金鑰（6位元組）。 隱含定義的主索引鍵問題是您沒有控制權。 此外，隱含值會針對沒有主索引鍵的所有表格進行全域指派。 如果您同時在這些資料表上執行寫入，此設定可能會導致爭用問題。 這可能會導致效能問題，因為表格也會共用全域隱藏的主要索引鍵索引增量。

為沒有任何主索引鍵的表格定義主索引鍵，以防止出現這些問題。

### 識別及更新沒有主索引鍵的表格

1. 使用下列SQL查詢識別沒有主索引鍵的表格：

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. 對於任何遺失主索引鍵的表格，請更新 `db_schema.xml` （宣告式綱要），其節點類似於以下內容：

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   新增節點時，請將 `referenceID` 和 `column name` 變數加上自訂自訂值。

如需詳細資訊，請參閱 [設定宣告式結構描述](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) （位於我們的開發人員檔案中）。

## 識別並移除重複索引

識別資料庫中的任何重複索引並將其移除。

### 檢查重複的索引

若要檢查Pro或Starter雲端架構上的重複索引，請執行下列SQL查詢。

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

查詢會傳回資料行名稱和任何重複索引的名稱。

Pro Architecture商家也可以使用Percona Toolkit來執行檢查  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` 命令。

### 移除重複的索引

使用SQL [DROP INDEX陳述式](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) 以移除重複的索引。

```SQL
DROP INDEX
```

## 其他資訊

[雲端部署的資料庫設定最佳實務](../planning/database-on-cloud.md)
