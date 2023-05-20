---
title: MySQL准則
description: 請依照下列步驟安裝和設定MySQL和MariaDB，以內部部署Adobe Commerce和Magento Open Source。
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# 一般MySQL准則

另請參閱 [系統需求](../../system-requirements.md) 支援的MySQL版本。

Adobe _強烈_ 建議您在設定資料庫時，遵循下列標準：

* Adobe Commerce和Magento Open Source使用 [MySQL資料庫觸發程式](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) 以改進重新索引期間的資料庫存取。 當索引器模式設定為時，就會建立這些模式 [排程](../../../configuration/cli/manage-indexers.md#configure-indexers). 應用程式不支援資料庫中的任何自訂觸發器，因為自訂觸發器可能會造成與未來Adobe Commerce和Magento Open Source版本不相容。
* 熟悉以下內容 [這些潛在的MySQL觸發條件限制](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) 然後再繼續。
* 若要增強您的資料庫安全性狀態，請啟用 [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL模式可防止儲存無效的資料值，這可能會造成不必要的資料庫互動。
* Adobe Commerce和Magento Open Source do _not_ 支援以MySQL陳述式為基礎的復寫。 請務必使用 _僅限_ [列式復寫](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce目前使用 `CREATE TEMPORARY TABLE` 交易內的陳述式，這些陳述式 [不相容](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) 對於資料庫實作，會使用以GTID為基礎的複製，例如 [Google Cloud SQL第二代執行個體](https://cloud.google.com/sql/docs/features#differences). 請考慮使用MySQL for Cloud SQL 8.0作為替代方案。

>[!NOTE]
>
>如果您的Web伺服器和資料庫伺服器位於不同的主機上，請在資料庫伺服器主機上執行本主題中討論的工作，然後請參閱 [設定遠端MySQL資料庫連線](mysql-remote.md).

## 在Ubuntu上安裝MySQL

Adobe Commerce和Magento Open Source2.4需要全新安裝MySQL 8.0。請依照下列連結取得在您的電腦上安裝MySQL的說明。

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

如果您預計會匯入大量產品，您可以將 [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) 大於預設值16 MB。

>[!NOTE]
>
>預設值適用於雲端基礎結構上的Adobe Commerce _和_ 內部部署專案。 雲端基礎結構上的Adobe Commerce Pro客戶必須開立支援工單，以增加 `max_allowed_packet` 值。 雲端基礎結構上的Adobe Commerce入門客戶可以更新 `/etc/mysql/mysql.cnf` 檔案。

若要增加值，請開啟 `/etc/mysql/mysql.cnf` 在文字編輯器中的檔案並找到 `max_allowed_packet`. 將變更儲存至 `mysql.cnf` 檔案，關閉文字編輯器，然後重新啟動MySQL (`service mysql restart`)。

若要選擇性地驗證您設定的值，請在 `mysql>` 提示：

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

然後， [設定資料庫執行處理](#configuring-the-database-instance).

## MySQL 8變更

針對Adobe Commerce和Magento Open Source2.4，我們新增對MySQL 8的支援。
本節說明開發人員應注意的MySQL 8重大變更。

### 已移除整數型別（內距）的寬度

MySQL 8.0.17已棄用整數資料型別(TINYINT、SMALLINT、MEDIUMINT、INT、BIGINT)的顯示寬度規格。在輸出中包含資料型別定義的陳述式不再顯示整數型別的顯示寬度，TINYINT(1)除外。 MySQL聯結器假設TINYINT(1)資料行是以BOOLEAN資料行起源。 此例外狀況可讓他們繼續做出該假設。

#### 範例

在mysql 8.19上說明admin_user

| 欄位 | 型別 | 空 | 金鑰 | 預設 | 額外 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | 否 | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | 是 |  | `NULL` |  |
| `lastname` | `varchar(32`) | 是 |  | `NULL` |  |
| `email` | `varchar(128)` | 是 |  | `NULL` |  |
| `username` | `varchar(40)` | 是 | UNI | `NULL` |  |
| `password` | `varchar(255)` | 否 |  | `NULL` |  |
| `created` | `timestamp` | 否 |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | 否 |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` 更新時 `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | 是 |  | `NULL` |  |
| `lognum` | `smallint unsigned` | 否 |  | `0` |  |

除了 _TINYINT(1)_，所有整數內距(TINYINT > 1、SMALLINT、MEDIUMINT、INT、BIGINT)應從 `db_schema.xml` 檔案。

如需詳細資訊，請參閱 [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### 預設ORDER BY行為

在8.0之前，專案都是依外部索引鍵排序。 預設排序順序取決於使用的引擎。
如果您的程式碼取決於特定排序，請一律指定排序順序。

### GROUP BY的已過時ASC和DESC限定詞

自MySQL 8.0.13起，已棄用 `ASC` 或 `DESC` 的限定詞 `GROUP BY` 子句已移除。 先前依賴的查詢 `GROUP BY` 排序可能會產生與先前MySQL版本不同的結果。 若要產生指定的排序順序，請提供 `ORDER BY` 子句。

## Commerce和MySQL 8

Adobe Commerce和Magento Open Source已進行一些變更，以正確支援MySQL 8。

### 查詢和插入行為

Adobe Commerce和Magento Open Source已透過在中設定SET SQL_MODE=&quot; ，停用一般驗證行為 `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. 停用驗證時，MySQL可能會截斷資料。 在MySQL中，查詢行為已變更： `Select * on my_table where IP='127.0.0.1'` 不再傳回結果，因為IP位址現在可正確視為字串而非整數。

## 從MySQL 5.7升級至MySQL 8

若要將MySQL從5.7版正確更新為8版，您必須依照下列順序執行步驟：

1. 將Adobe Commerce或Magento Open Source升級至2.4.0。測試所有內容，並確定您的系統可如預期般運作。
1. 啟用維護模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 進行資料庫備份：

   ```bash
   bin/magento setup:backup --db
   ```

1. 將MySQL更新至版本8。
1. 將備份資料匯入MySQL。
1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 停用維護模式：

   ```bash
   bin/magento maintenance:disable
   ```

## 設定資料庫執行處理

本節說明如何建立Adobe Commerce或Magento Open Source的資料庫執行個體。 雖然建議使用新資料庫執行個體，但您可以選擇安裝Adobe Commerce或與現有資料庫執行個體進行Magento Open Source。

設定MySQL資料庫執行處理：

1. 以任何使用者身分登入您的資料庫伺服器。
1. 前往MySQL命令提示字元：

   ```bash
   mysql -u root -p
   ```

1. 輸入MySQL `root` 提示時的使用者密碼。
1. 按照顯示的順序輸入以下命令，以建立名為的資料庫執行處理 `magento` 使用使用者名稱 `magento`：

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. 輸入 `exit` 結束命令提示字元。

1. 驗證資料庫：

   ```bash
   mysql -u magento -p
   ```

   如果顯示MySQL監督器，表示您已正確建立資料庫。 如果顯示錯誤，請重複上述命令。

1. 如果您的Web伺服器和資料庫伺服器位於不同的主機上，請在資料庫伺服器主機上執行本主題中討論的工作，然後請參閱 [設定遠端MySQL資料庫連線](mysql-remote.md).

   建議您根據業務需要設定適當的資料庫執行個體。 設定資料庫時，請記住下列事項：

   * 索引器需要較高的值 `tmp_table_size` 和 `max_heap_table_size` 值（例如64 M）。 如果您設定 `batch_size` 引數，您可以隨著表格大小設定調整該值，以改善索引器效能。 請參閱 [Optimization指南](../../../performance/configuration.md) 以取得詳細資訊。

   * 為獲得最佳效能，請確定所有MySQL和Adobe Commerce或Magento Open Source索引表都可以儲存在記憶體中(例如，設定 `innodb_buffer_pool_size`)。

   * 與其他MariaDB或MySQL版本相比，在MariaDB 10.4上重新索引需要更多時間。 另請參閱 [設定最佳實務](../../../performance/configuration.md#indexers).

1. 適用於MySQL `TIMESTAMP` 依應用程式的宣告式結構描述架構（系統變數）所預期的偏好設定和構成來遵循的欄位 `explicit_defaults_for_timestamp` 必須設定為 `on`.

   引用：

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   如果未啟用此設定， `bin/magento setup:db:status` 一律會報告 `Declarative Schema is not up to date`.

>[!NOTE]
>
>此 `explicit_defaults_for_timestamp` 設定已過時。 此設定可控制將在未來MySQL發行版本中移除的已棄用TIMESTAMP行為。 移除這些行為時， `explicit_defaults_for_timestamp` 設定也會移除。

>[!WARNING]
>
>對於雲端基礎結構專案的Adobe Commerce， `explicit_defaults_for_timestamp` MySQL (MariaDB)的設定預設為 _關閉_.

{{$include /help/_includes/maria-db-config.md}}
