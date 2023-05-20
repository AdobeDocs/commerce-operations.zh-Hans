---
title: 雲端部署的資料庫設定最佳實務
description: 瞭解如何在雲端基礎結構上部署Adobe Commerce時，設定資料庫和應用程式設定以改善效能。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---

# 資料庫組態的最佳實務

瞭解在雲端基礎結構上部署Adobe Commerce時，改善資料庫效能和有效使用資料庫的最佳實務。

## 受影響的產品

雲端基礎結構上的Adobe Commerce

## 將所有MyISAM表格轉換為InnoDB

Adobe建議使用InnoDB資料庫引擎。 在預設的Adobe Commerce安裝中，資料庫中的所有表格都是使用InnoDB引擎儲存的。 不過，某些協力廠商模組（擴充功能）可能會引入MyISAM格式的表格。 安裝協力廠商模組後，請檢查資料庫以識別中的任何表格 `myisam` 格式化並轉換為 `innodb` 格式。

### 判斷模組是否包含MyISAM表格

您可以先分析協力廠商模組程式碼，再進行安裝，以判斷其是否使用MyISAM表格。

如果您已安裝擴充功能，請執行以下查詢來判斷資料庫是否有任何MyISAM表格：

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### 將儲存引擎變更為InnoDB

在 `db_schema.xml` 檔案宣告表格，設定 `engine` 對應專案的屬性值 `table` 節點至 `innodb`. 如需參考資訊，請參閱 [設定宣告式結構描述>表格節點](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) （位於我們的開發人員檔案中）。

宣告式配置是在Adobe Commerce的雲端基礎結構2.3版中引入。

## 設定原生MySQL搜尋的建議搜尋引擎

Adobe建議您一律在雲端基礎結構專案中為您的Adobe Commerce設定Elasticsearch或OpenSearch，即使您計畫為您的Adobe Commerce應用程式設定協力廠商搜尋工具亦然。 此設定會提供後援選項，以防協力廠商搜尋工具失敗。

您使用的搜尋引擎取決於所安裝的雲端版本Adobe Commerce：

- 若是Adobe Commerce 2.4.4和更新版本，請使用OpenSearch服務進行原生MySQL搜尋。

- 若是較舊的Adobe Commerce版本，請使用Elasticsearch。

若要判斷目前使用中的搜尋引擎，請執行以下命令：

```bash
./bin/magento config:show catalog/search/engine
```

如需設定指示，請參閱雲端上Adobe Commerce的開發人員指南：

- [設定OpenSearch服務](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [設定Elasticsearch服務](https://devdocs.magento.com/cloud/project/services-elastic.html)

## 避免自訂觸發器

儘可能避免使用自訂觸發器。

觸發器用於將變更記錄到稽核表中。 Adobe建議將應用程式設定為直接寫入稽核表格，而非使用觸發功能，原因如下：

- 觸發器會解譯為程式碼，而MySQL不會預先編譯它們。 掛接至查詢的交易空間時，會為使用表格執行的每個查詢新增剖析器和解譯器的額外負荷。
- 觸發程式與原始查詢共用相同的交易空間，當這些查詢爭奪表格上的鎖定時，觸發程式會獨立爭奪其他表格上的鎖定。

若要瞭解使用自訂觸發器的替代方案，請參閱 [有效使用MySQL觸發程式](mysql-triggers-usage.md) 在我們的支援知識庫中。

## 升級 [!DNL ECE-Tools] 至2002.0.21版或更新版本 {#ece-tools-version}

若要避免cron死鎖的潛在問題，請將ECE-Tools升級至2002.0.21版或更新版本。 如需指示，請參閱 [更新 `ece-tools` 版本](https://devdocs.magento.com/cloud/project/ece-tools-update.html) （位於我們的開發人員檔案中）。

## 安全地切換索引器模式

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

切換索引器會產生 [!DNL data definition language] (DDL)陳述式來建立可能導致資料庫鎖定的觸發器。 您可以在變更設定前，先將網站置於維護模式並停用cron工作，即可避免此問題。
如需指示，請參閱 [設定索引子](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) 在 *Adobe Commerce設定指南*.

## 請勿在生產環境中執行DDL陳述式

請避免在生產環境中執行DDL陳述式，以避免衝突（例如表格修改和建立）。 此 `setup:upgrade` 程式是個例外。

如果您需要執行DDL陳述式，請將網站置於維護模式並停用cron （請參閱上一節中有關安全切換索引的說明）。

## 啟用訂單封存

啟用管理員的訂單封存，以隨著訂單資料成長，減少銷售表格所需的空間。 封存可節省MySQL磁碟空間並改善簽出效能。

另請參閱 [啟用封存](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) Adobe Commerce商家檔案內。

## 其他資訊

- [MySQL儲存引擎](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [MariaDB的Adobe Commerce 2.3.5升級先決條件](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [解決資料庫效能問題的最佳實務](../maintenance/resolve-database-performance-issues.md)
