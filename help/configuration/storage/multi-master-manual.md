---
title: 手动配置主控数据库
description: 请参阅有关手动配置拆分数据库解决方案的指南。
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 0%

---


# 手动配置主控数据库

{{ee-only}}

{{deprecate-split-db}}

如果商务应用程序已在生产中，或者如果您已安装自定义代码或组件，则可能需要手动配置拆分数据库。 在继续操作之前，请联系Adobe Commerce支持部门，以了解在您的情况下是否需要此操作。

手动拆分数据库涉及：

- 创建 [结账](https://glossary.magento.com/checkout) 和订单管理系统(OMS)数据库
- 运行一系列SQL脚本，这些脚本：

   - 删除外键
   - 备份销售和报价数据库表
   - 将表从主数据库移动到销售数据库和报价数据库

>[!WARNING]
>
>如果任何自定义代码在销售数据库和报价数据库中的表中使用JOIN，则 _无法_ 使用拆分数据库。 如有疑问，请联系任何自定义代码或扩展的作者，以确保其代码不使用JOIN。

本主题使用以下命名约定：

- 主数据库名称为 `magento` 其用户名和密码都 `magento`
- 报价数据库名称为 `magento_quote` 其用户名和密码都 `magento_quote`

   报价数据库也称为 _结账_ 数据库。

- 销售数据库名称为 `magento_sales` 其用户名和密码都 `magento_sales`

   销售数据库也称为OMS数据库。

>[!INFO]
>
>本指南假定所有三个数据库都与Commerce应用程序位于同一台主机上。 但是，数据库的位置及其名称的选择取决于您。 我们希望这些示例能够更方便地遵循相关说明。

## 备份商务系统

Adobe强烈建议您备份当前的数据库和文件系统，以便在此过程中遇到问题时可以恢复它。

**备份系统**:

1. 作为或切换到 [文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 输入以下命令：

   ```bash
   magento setup:backup --code --media --db
   ```

1. 继续下一节。

## 设置其他主控数据库

本节将讨论如何为销售和 [报价](https://glossary.magento.com/quote) 表格。

**创建销售和OMS报价数据库**:

1. 以任何用户身份登录数据库服务器。
1. 输入以下命令以转到MySQL命令提示符：

   ```bash
   mysql -u root -p
   ```

1. 输入MySQL `root` 用户的密码。
1. 按照创建名为的数据库实例的顺序输入以下命令 `magento_quote` 和 `magento_sales` 使用相同的用户名和密码：

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. 输入 `exit` 退出命令提示符。

1. 每次验证一个数据库：

   报价数据库：

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

   如果显示MySQL监视器，则表示您已正确创建了数据库。 如果显示错误，请重复上述命令。

1. 继续下一节。

## 配置销售数据库

本节讨论如何创建和运行SQL脚本，这些脚本会更改引号数据库表并备份这些表中的数据。

销售数据库表名以下列项开头：

- `salesrule_`
- `sales_`
- `magento_sales_`
- 的 `magento_customercustomattributes_sales_flat_order` 表格也会受到影响

>[!INFO]
>
>本节包含具有特定数据库表名称的脚本。 如果您已执行自定义，或者希望在对表执行操作之前查看表的完整列表，请参阅 [引用脚本](#reference-scripts).

有关更多信息，请参阅：

- [创建销售数据库SQL脚本](#create-sales-database-sql-scripts)
- [备份销售数据](#back-up-sales-data)

### 创建销售数据库SQL脚本

在用户可访问的位置创建以下SQL脚本，当您登录到Commerce Server时，该位置可供用户访问。 例如，如果您以 `root`，您可以在 `/root/sql-scripts` 目录访问Advertising Cloud的帮助。

#### 删除外键

此脚本从销售数据库中删除引用非销售表的外键。

创建以下脚本，并为其命名，如 `1_foreign-sales.sql`. 替换 `<your main DB name>` 的名称。

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

### 配置销售数据库

运行上述脚本：

1. 以 `root` 或管理用户：

   ```bash
   mysql -u root -p
   ```

1. 在 `mysql>` 提示，按如下方式运行脚本：

   ```shell
   source <path>/<script>.sql
   ```

   例如，

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. 运行脚本后，输入 `exit`.

### 备份销售数据

本节将讨论如何从主Commerce数据库备份销售表，以便在单独的销售数据库中还原它们。

如果您当前位于 `mysql>` 提示，输入 `exit` 返回命令shell。

运行以下 `mysqldump` 命令，一次一个命令。 在每个示例中，使用以下代码：

- `<your database root username>` 数据库根用户的名称
- `<your database root user password>` 和用户密码
- `<your main Commerce DB name>` 的名称
- `<path>` 具有可写文件系统路径

#### 脚本1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### 脚本2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### 脚本3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### 脚本4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### 恢复销售数据

此脚本将还原报价数据库中的销售数据。

#### NDB要求

如果您使用 [网络数据库(NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) 群集：

1. 在转储文件中，将表从InnoDb转换为NDB类型：

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. 由于NDB表不支持FULLTEXT，因此从转储中删除具有FULLTEXT键的行。

#### 恢复数据

运行以下命令：

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

其中

- `<your sales DB name>` 的名称。

   在本主题中，示例数据库名称为 `magento_sales`.

- `<root username>` 和您的MySQL根用户名
- `<root user password>` 和用户密码
- 验证您之前创建的备份文件的位置(例如， `/var/sales.sql`)

## 配置报价数据库

本节讨论从销售数据库表中删除外键和将表移动到销售数据库所需的任务。

>[!INFO]
>
>本节包含具有特定数据库表名称的脚本。 如果您已执行自定义，或者希望在对表执行操作之前查看表的完整列表，请参阅 [引用脚本](#reference-scripts).

引用数据库表名称以开头 `quote`. 的 `magento_customercustomattributes_sales_flat_quote` 和 `magento_customercustomattributes_sales_flat_quote_address` 表也受到影响

### 从引号表中删除外键

此脚本从引号表中删除引用非引号表的外键。 替换 `<your main Commerce DB name>` 的名称。

创建以下脚本，并为其命名，如 `2_foreign-key-quote.sql`:

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

按如下方式运行脚本：

1. 以根用户或管理用户身份登录MySQL数据库：

   ```bash
   mysql -u root -p
   ```

1. 在 `mysql >` 提示，按如下方式运行脚本：
   `source <path>/<script>.sql`

   例如，

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. 脚本运行后，输入 `exit`.

### 备份报价表

本节讨论如何从主数据库备份报价表并在报价数据库中还原这些报价表。

在命令提示符下运行以下命令：

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### NDB要求

如果您使用 [网络数据库(NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) 群集：

1. 在转储文件中，将表从InnoDb转换为NDB类型：

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. 由于NDB表不支持FULLTEXT，因此从转储中删除具有FULLTEXT键的行。

### 将表还原到报价数据库

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## 从数据库中删除销售和报价表

此脚本销售表和报价表来自商务数据库。 替换 `<your main DB name>` 的名称。

创建以下脚本，并为其命名，如 `3_drop-tables.sql`:

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

按如下方式运行脚本：

1. 以根用户或管理用户身份登录MySQL数据库：

   ```bash
   mysql -u root -p
   ```

1. 在 `mysql>` 提示，按如下方式运行脚本：

   ```shell
   source <path>/<script>.sql
   ```

   例如，

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. 脚本运行后，输入 `exit`.

## 更新部署配置

手动拆分数据库的最后一步是向Commerce的部署配置中添加连接和资源信息， `env.php`.

要更新部署配置，请执行以下操作：

1. 作为或切换到 [文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. 备份部署配置：

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. 打开 `<magento_root>/app/etc/env.php` 在文本编辑器中，使用以下部分中讨论的准则更新该编辑器。

### 更新数据库连接

找到以开头的块 `'default'` (在 `'connection'`)和添加 `'checkout'` 和 `'sales'` 中。 将示例值替换为适合您网站的值。

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

### 更新资源

找到以开头的块 `'resource'` 添加 `'checkout'` 和 `'sales'` 部分如下：

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

## 引用脚本

此部分提供了脚本，您可以运行这些脚本来打印受影响表的完整列表，而无需对它们执行任何操作。 在手动拆分数据库之前，可以使用它们查看哪些表受到了影响，如果您使用自定义 [数据库模式](https://glossary.magento.com/database-schema).

要使用这些脚本，请执行以下操作：

1. 使用本节中每个脚本的内容创建一个SQL脚本。
1. 在每个脚本中，替换 `<your main DB name>` 的名称。

   在本主题中，示例数据库名称为 `magento`.

1. 从 `mysql>` 提示为 `source <script name>`
1. 检查输出。
1. 将每个脚本的结果复制到另一个SQL脚本，删除管道字符(`|`)。
1. 从 `mysql>` 提示为 `source <script name>`.

   运行此第二个脚本将在主商务数据库中执行操作。

### 删除外键（销售表）

此脚本从销售数据库中删除引用非销售表的外键。

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

### 删除外键（引号表）

此脚本从引号表中删除引用非引号表的外键。

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

### 删除销售表

此脚本从Commerce数据库中删除销售表。

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

### 下拉报价表

删除以 `quote_`.