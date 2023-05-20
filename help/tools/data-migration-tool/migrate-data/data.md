---
title: 移轉資料
description: 瞭解如何透過開始將資料從Magento1移轉至Magento2 [!DNL Data Migration Tool].
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# 移轉資料

開始之前，請採取下列步驟進行準備：

1. 以下列身分登入您的應用程式伺服器： [檔案系統擁有者](../../../installation/prerequisites/file-system/overview.md).
1. 變更至應用程式安裝目錄，或確認已將其新增至您的系統 `PATH`.

請參閱 [首要步驟](overview.md#first-steps) 區段以取得更多詳細資料。

## 執行資料移轉命令

若要開始移轉資料，請執行：

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-a|--auto]` 是選用引數，可防止移轉在遇到完整性檢查錯誤時停止。

* `[-r|--reset]` 是從頭開始移轉的可選引數。 您可以使用此引數來測試移轉。

* `{<path to config.xml>}` 為的絕對檔案系統路徑 `config.xml`；此引數為必要項

在此步驟中， [!DNL Data Migration Tool] 為Magento1資料庫中的移轉表格建立其他表格和觸發程式。 它們用於 [增量/差異](delta.md) 移轉步驟。 其他表格包含最終移轉執行後變更記錄的相關資訊。 資料庫觸發程式用於填入這些額外表格，因此，如果正在特定表格上執行新作業（新增/修改/移除記錄），這些資料庫觸發程式會將此作業的相關資訊儲存至額外表格。 當我們執行差異移轉程式時， [!DNL Data Migration Tool] 檢查這些表格中是否有未處理的記錄，並將必要的內容移轉到Magento2資料庫。

每個新表格都包含：

* `m2_cl` 前置詞
* `INSERT`， `UPDATE`， `DELETE` 事件觸發程式。

例如，對於 `sales_flat_order` 此 [!DNL Data Migration Tool] 建立：

* `m2_cl_sales_flat_order` 表格：

   ```sql
   CREATE TABLE `m2_cl_sales_flat_order` (
     `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
     `operation` text COMMENT 'Operation',
     `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
     PRIMARY KEY (`entity_id`)
   ) COMMENT='m2_cl_sales_flat_order';
   ```

* `trg_sales_flat_order_after_insert`， `trg_sales_flat_order_after_update`， `trg_sales_flat_order_after_delete` 觸發器：

   ```sql
   DELIMITER ;;
   CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
     FOR EACH ROW
     BEGIN
      INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
     END
   ;;
   
   DELIMITER ;;
   CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
     FOR EACH ROW
     BEGIN
      INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
     END
   ;;
   
   DELIMITER ;;
   CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
     FOR EACH ROW
     BEGIN
      INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
     END
   ;;
   ```

>[!NOTE]
>
>此 [!DNL Data Migration Tool] 在執行時儲存目前的進度。 如果錯誤或使用者介入導致其停止執行，則工具會在最後已知的良好狀態繼續進度。 強制執行 [!DNL Data Migration Tool] 若要從頭開始執行，請使用 `--reset` 引數。 在這種情況下，建議您還原Magento2資料庫傾印，以防止複製先前移轉的資料。


## 可能的一致性錯誤

執行時， [!DNL Data Migration Tool] 可能會報告Magento1和Magento2資料庫之間的不一致，並顯示如下訊息：

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

請參閱 [疑難排除](https://support.magento.com/hc/en-us/articles/360033020451) 區段，以取得詳細資訊和建議。

## 下一個移轉步驟

[移轉變更](delta.md)
