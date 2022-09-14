---
title: 迁移数据
description: 了解如何开始将数据从Magento1迁移到Magento2，使用 [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# 迁移数据

在开始之前，请采取以下步骤进行准备：

1. 以下身份登录到应用程序服务器： [文件系统所有者](../../../installation/prerequisites/file-system/overview.md).
1. 更改到应用程序安装目录，或确保将其添加到系统 `PATH`.

请参阅 [首要步骤](overview.md#first-steps) 部分以了解更多详细信息。

## 运行数据迁移命令

要开始迁移数据，请运行：

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-a|--auto]` 是一个可选参数，可阻止迁移在遇到完整性检查错误时停止。

* `[-r|--reset]` 是从头开始迁移的可选参数。 您可以使用此参数测试迁移。

* `{<path to config.xml>}` 是 `config.xml`;此参数是必需的

在此步骤中， [!DNL Data Migration Tool] 为Magento1数据库中的迁移表创建其他表和触发器。 在 [增量/增量](delta.md) 迁移步骤。 其他表包含有关最终迁移执行后更改记录的信息。 数据库触发器用于填充这些额外表，因此，如果正在对特定表执行新操作（添加/修改/删除记录），则这些数据库触发器会将有关此操作的信息保存到额外表。 运行增量迁移过程时， [!DNL Data Migration Tool] 检查这些表是否有未处理的记录，并将必要的内容迁移到Magento2数据库。

每个新表都包含：

* `m2_cl` 前缀
* `INSERT`, `UPDATE`, `DELETE` 事件触发器。

例如，对于 `sales_flat_order` the [!DNL Data Migration Tool] 创建：

* `m2_cl_sales_flat_order` 表：

   ```sql
   CREATE TABLE `m2_cl_sales_flat_order` (
     `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
     `operation` text COMMENT 'Operation',
     `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
     PRIMARY KEY (`entity_id`)
   ) COMMENT='m2_cl_sales_flat_order';
   ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` 触发器：

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
>的 [!DNL Data Migration Tool] 在运行时保存其当前进度。 如果错误或用户干预阻止该工具运行，则该工具将恢复上次已知正常状态的进度。 强制 [!DNL Data Migration Tool] 要从头开始运行，请使用 `--reset` 参数。 在这种情况下，我们建议您恢复Magento2数据库转储，以防止复制以前迁移的数据。


## 可能的一致性错误

运行时， [!DNL Data Migration Tool] 可能报告Magento1和Magento2数据库之间的不一致，并显示如下消息：

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

请参阅 [疑难解答](https://support.magento.com/hc/en-us/articles/360033020451) 部分以了解更多信息和建议。

## 下一迁移步骤

[迁移更改](delta.md)