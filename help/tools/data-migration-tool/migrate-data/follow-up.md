---
title: 数据迁移跟进
description: 了解如何验证Magento1到Magento2的数据迁移是否成功，以及所有功能是否均可按预期运行。
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 数据迁移跟进

Magento1的某些行为和逻辑在Magento2中的实现方式不同。 此 [!DNL Data Migration Tool] 搞定它。 有一些迁移方面是您应当了解的，有时，您必须执行一些次要步骤，以便某些功能在迁移之后能够顺利工作。

## 信息

### 不支持拆分数据库

此 [!DNL Data Migration Tool] 不支持拆分数据库。

### 组价格转换为层价格

在迁移期间，所有组价格都会自动转换为层价格。

### 销售实体的新编号

按原样迁移订单、发票、发运、贷项通知单和RMA的参考编号。 迁移后，将应用新的Magento2编号分配规则。 新销售实体的数字不同。

## 步骤

### 重新保存客户区段 [仅限Adobe Commerce]

迁移后，必须从管理面板中重新保存客户区段才能使其启动并运行。

### 配置时区

该工具不会迁移时区设置，因此您必须在迁移后手动配置时区。 **商店** > **配置** > **区域设置选项** > **时区**.

默认情况下，Magento在数据库的UTC-0区域中存储时间数据，并根据当前时区设置显示这些数据。 如果时间数据已保存在数据库的UTC-0以外的区域中，则必须使用将现有时间转换为UTC-0 [!DNL Data Migration Tool]的 `\Migration\Handler\Timezone` 处理程序。

在以下示例中，Magento1在数据库的UTC-7区域中错误地节省了时间（例如，由于第三方扩展错误）。 要在迁移时将客户帐户创建时间正确转换为UTC-0区域，请执行以下步骤：

1. 复制 `map-customer.xml.dist` 配置文件从的相应目录 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`)到 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` 文件。

1. 更新 `<customer_map_file>` 中的节点 `config.xml` 并移除 `.dist` 扩展自 `map-customer.xml.dist`

1. 将以下规则添加到 `map-customer.xml` 文件：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```
