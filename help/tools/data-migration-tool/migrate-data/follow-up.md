---
title: 数据迁移跟进
description: 了解如何验证您的Magento1到Magento2数据迁移是否成功，以及所有功能是否按预期运行。
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# 数据迁移跟进

在Magento2中，Magento1的某些行为和逻辑实施方式有所不同。 的 [!DNL Data Migration Tool] 好好照顾。 您应该了解一些迁移方面，有时您必须执行一些小步骤，某些功能才能在迁移后顺利运行。

## 信息

### 不支持拆分数据库

的 [!DNL Data Migration Tool] 不支持拆分数据库。

### 转换为层价的组价格

在迁移期间，所有组价格都会自动转换为层价格。

### 销售实体的新编号

订单、发票、发运、贷项通知单和RMA的参考编号按原样迁移。 迁移后，将应用新的Magento2号分配规则。 新销售实体的数值不同。

## 步骤

### 重新保存客户区段 [仅Adobe Commerce]

迁移后，必须从 [管理员](https://glossary.magento.com/admin) 启动并运行的面板。

### 配置时区

该工具不会迁移时区设置，因此迁移后，您必须在 **商店** > **配置** > **区域设置选项** > **时区**.

默认情况下，Magento将时间数据以UTC-0区域的形式存储在数据库中，并根据当前时区设置显示数据。 如果时间数据已保存在数据库中UTC-0以外的区域，则必须使用 [!DNL Data Migration Tool]&#39;s `\Migration\Handler\Timezone` 处理程序。

在以下示例中，Magento1在数据库的UTC-7区域中错误地节省了时间（例如，由于第三方扩展错误）。 要在迁移时将客户帐户创建时间正确转换为UTC-0区域，请执行以下步骤：

1. 复制 `map-customer.xml.dist` 配置文件 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`)到 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` 文件。

1. 更新 `<customer_map_file>` 节点 `config.xml` 并删除 `.dist` 扩展 `map-customer.xml.dist`

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
