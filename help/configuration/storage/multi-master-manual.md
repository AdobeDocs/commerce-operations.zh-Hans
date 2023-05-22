---
title: 手動設定主資料庫
description: 請參閱手動設定分割資料庫解決方案的指南。
recommendations: noCatalog
exl-id: 2c357486-4a8a-4a36-9e13-b53c83f69456
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 0%

---

# 手動設定主資料庫

{{ee-only}}

{{deprecate-split-db}}

如果Commerce應用程式已在生產環境中，或您已安裝自訂程式碼或元件，則可能需要手動設定分割資料庫。 在繼續之前，請聯絡Adobe Commerce支援，檢視這對您而言是否必要。

手動分割資料庫涉及：

- 建立結帳與訂單管理系統(OMS)資料庫
- 執行一系列SQL指令碼，這些指令碼會：

   - 放置外部索引鍵
   - 備份銷售與報價資料庫表格
   - 將表格從主要資料庫移至銷售和報價資料庫

>[!WARNING]
>
>如果任何自訂程式碼使用JOINs搭配sales和quote資料庫中的表格，則您 _無法_ 使用分割資料庫。 如有疑問，請聯絡任何自訂程式碼或擴充功能的作者，確保其程式碼不會使用JOIN。

本主題使用下列命名慣例：

- 主要資料庫名稱為 `magento` 及其使用者名稱和密碼都是 `magento`
- 引號資料庫名稱是 `magento_quote` 及其使用者名稱和密碼都是 `magento_quote`

   報價資料庫也稱為 _簽出_ 資料庫。

- 銷售資料庫名稱為 `magento_sales` 及其使用者名稱和密碼都是 `magento_sales`

   銷售資料庫也稱為OMS資料庫。

>[!INFO]
>
>本指南假設所有三個資料庫與Commerce應用程式位於相同主機上。 不過，您可以自行選擇資料庫的所在位置及其命名名稱。 我們希望我們的範例能讓指示更容易遵循。

## 備份商務系統

Adobe強烈建議您備份目前的資料庫和檔案系統，以便在處理過程中遇到問題時進行還原。

**備份您的系統**：

1. 以或切換為身分登入您的Commerce伺服器， [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 輸入下列命令：

   ```bash
   magento setup:backup --code --media --db
   ```

1. 繼續下一節。

## 設定其他主要資料庫

本節說明如何建立銷售與報價表的資料庫執行處理。

**建立銷售和OMS報價資料庫**：

1. 以任何使用者身分登入您的資料庫伺服器。
1. 輸入下列命令以進入MySQL命令提示字元：

   ```bash
   mysql -u root -p
   ```

1. 輸入MySQL `root` 提示時的使用者密碼。
1. 按照顯示的順序輸入以下命令，以建立名為的資料庫執行處理 `magento_quote` 和 `magento_sales` 相同的使用者名稱和密碼：

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. 輸入 `exit` 結束命令提示字元。

1. 逐一驗證資料庫：

   報價資料庫：

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   如果顯示MySQL監督器，表示您已正確建立資料庫。 如果顯示錯誤，請重複上述命令。

1. 繼續下一節。

## 設定銷售資料庫

本節說明如何建立及執行SQL命令檔，以變更引號資料庫表格，並備份這些表格的資料。

Sales資料庫表格名稱的開頭為：

- `salesrule_`
- `sales_`
- `magento_sales_`
- 此 `magento_customercustomattributes_sales_flat_order` 表格也會受到影響

>[!INFO]
>
>此段落包含具有特定資料庫表格名稱的命令檔。 如果您已執行自訂，或想在表格上執行動作之前先檢視完整的表格清單，請參閱 [參考指令碼](#reference-scripts).

如需詳細資訊，請參閱：

- [建立銷售資料庫SQL命令檔](#create-sales-database-sql-scripts)
- [備份銷售資料](#back-up-sales-data)

### 建立銷售資料庫SQL命令檔

在您登入Commerce伺服器的使用者可存取的位置，建立下列SQL指令碼。 例如，如果您登入或執行命令為 `root`，您可在以下位置建立指令碼： `/root/sql-scripts` 目錄。

#### 移除外部索引鍵

此指令碼會從銷售資料庫中移除參照非銷售資料表的外來鍵。

建立以下指令碼，並命名如下 `1_foreign-sales.sql`. Replace `<your main DB name>` 使用資料庫名稱。

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### 設定銷售資料庫

執行前面的指令碼：

1. 以以下身分登入您的MySQL資料庫： `root` 或管理使用者：

   ```bash
   mysql -u root -p
   ```

1. 在 `mysql>` 提示，請依照以下方式執行指令碼：

   ```shell
   source <path>/<script>.sql
   ```

   例如，

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. 指令碼執行後，輸入 `exit`.

### 備份銷售資料

本節說明如何從主要Commerce資料庫備份銷售表格，以便在個別的銷售資料庫中還原它們。

如果您目前在 `mysql>` 提示，輸入 `exit` 以返回命令shell。

執行以下命令 `mysqldump` 命令shell中的命令，一次一個命令。 在每一個中，取代下列內容：

- `<your database root username>` 使用資料庫根使用者名稱
- `<your database root user password>` 使用使用者密碼
- `<your main Commerce DB name>` 包含Commerce資料庫名稱
- `<path>` 具有可寫入的檔案系統路徑

#### 指令碼1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### 指令碼2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### 指令碼3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### 指令碼4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### 還原銷售資料

此指令碼會還原報價資料庫中的銷售資料。

#### NDB需求

如果您使用 [網路資料庫(NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) 叢集：

1. 將傾印檔案中的表格從InnoDb轉換為NDB型別：

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. 從傾印中移除具有FULLTEXT索引鍵的列，因為NDB表格不支援FULLTEXT。

#### 還原資料

執行以下命令：

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

位置

- `<your sales DB name>` 與您的銷售資料庫名稱搭配使用。

   在此主題中，範例資料庫名稱為 `magento_sales`.

- `<root username>` 使用您的MySQL根使用者名稱
- `<root user password>` 使用使用者密碼
- 驗證您先前建立的備份檔案的位置(例如， `/var/sales.sql`)

## 設定報價資料庫

本節討論從sales資料庫表格刪除外部索引鍵，並將表格移動到sales資料庫所需的工作。

>[!INFO]
>
>此段落包含具有特定資料庫表格名稱的命令檔。 如果您已執行自訂，或想在表格上執行動作之前先檢視完整的表格清單，請參閱 [參考指令碼](#reference-scripts).

引號資料庫表格名稱的開頭為 `quote`. 此 `magento_customercustomattributes_sales_flat_quote` 和 `magento_customercustomattributes_sales_flat_quote_address` 表格也會受到影響

### 從引號表格中卸除外部索引鍵

此指令碼會從引號表格中移除參照非引號表格的外部索引鍵。 Replace `<your main Commerce DB name>` ，並使用您的Commerce資料庫名稱。

建立以下指令碼，並命名如下 `2_foreign-key-quote.sql`：

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

執行指令碼，如下所示：

1. 以root或管理使用者身分登入MySQL資料庫：

   ```bash
   mysql -u root -p
   ```

1. 在 `mysql >` 提示，請依照以下方式執行指令碼：
   `source <path>/<script>.sql`

   例如，

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. 指令碼執行後，輸入 `exit`.

### 備份報價表

本節說明如何從主要資料庫備份報價表，並將它們還原到報價資料庫中。

從命令提示字元執行下列命令：

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### NDB需求

如果您使用 [網路資料庫(NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) 叢集：

1. 將傾印檔案中的表格從InnoDb轉換為NDB型別：

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. 從傾印中移除具有FULLTEXT索引鍵的列，因為NDB表格不支援FULLTEXT。

### 將表格還原至報價資料庫

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## 從資料庫卸除銷售和報價表

此指令碼會從Commerce資料庫中編寫sales和quote表格。 Replace `<your main DB name>` ，並使用您的Commerce資料庫名稱。

建立以下指令碼，並命名如下 `3_drop-tables.sql`：

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

執行指令碼，如下所示：

1. 以root或管理使用者身分登入MySQL資料庫：

   ```bash
   mysql -u root -p
   ```

1. 在 `mysql>` 提示，請依照以下方式執行指令碼：

   ```shell
   source <path>/<script>.sql
   ```

   例如，

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. 指令碼執行後，輸入 `exit`.

## 更新您的部署設定

手動分割資料庫的最後一步是將連線和資源資訊新增到Commerce的部署設定， `env.php`.

若要更新部署設定：

1. 以或切換為身分登入您的Commerce伺服器， [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 備份您的部署設定：

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. 開啟 `<magento_root>/app/etc/env.php` 使用下節中討論的指南進行更新。

### 更新資料庫連線

找出區塊，從 `'default'` (在 `'connection'`)並新增 `'checkout'` 和 `'sales'` 區段。 將範例值取代為您的網站適當的值。

```php
 'default' =>
      array (
'host' => 'localhost',
'dbname' => 'magento',
'username' => 'magento',
'password' => 'magento',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### 更新資源

找出區塊，從 `'resource'` 並新增 `'checkout'` 和 `'sales'` 區段如下所示：

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## 參考指令碼

本節提供您可以執行的指令碼，這些指令碼可列印受影響表格的完整清單，而不需對其執行任何動作。 在手動分割資料庫之前，您可以使用它們來檢視哪些表格會受到影響，如果您使用自訂資料庫綱要的擴充功能，這會很有用。

若要使用這些指令碼：

1. 建立一個SQL命令檔，其中包含本節中每個命令檔的內容。
1. 在每個指令碼中，取代 `<your main DB name>` ，並使用您的Commerce資料庫名稱。

   在此主題中，範例資料庫名稱為 `magento`.

1. 從以下位置執行每個指令碼： `mysql>` 提示為 `source <script name>`
1. 檢查輸出。
1. 將每個指令碼的結果複製到另一個SQL指令碼，移除垂直號字元(`|`)。
1. 從以下位置執行每個指令碼： `mysql>` 提示為 `source <script name>`.

   執行此第二個指令碼會執行主要Commerce資料庫中的動作。

### 移除外部索引鍵（銷售表格）

此指令碼會從銷售資料庫中移除參照非銷售資料表的外來鍵。

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### 移除外部索引鍵（引號表格）

此指令碼會從引號表格中移除參照非引號表格的外部索引鍵。

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### 卸除銷售表格

此指令碼會從Commerce資料庫捨棄銷售表格。

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### 卸除引號表格

拖放開頭為的所有表格 `quote_`.
