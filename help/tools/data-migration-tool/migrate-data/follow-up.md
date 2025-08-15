---
title: 数据迁移跟进
description: 了解如何验证Magento 1到Magento 2的数据迁移是否成功，以及所有功能是否均可按预期运行。
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# 数据迁移跟进

Magento 1的某些行为和逻辑在Magento 2中的实施方式有所不同。 [!DNL Data Migration Tool]会处理此工作。 有一些迁移方面是您应当了解的，有时，您必须执行一些次要步骤，以便某些功能在迁移之后能够顺利工作。

## 信息

### 不支持拆分数据库

[!DNL Data Migration Tool]不支持拆分数据库。

### 组价格转换为层价格

在迁移期间，所有组价格都会自动转换为层价格。

### 销售实体的新编号

按原样迁移订单、发票、发运、贷项通知单和RMA的参考编号。 迁移后，将应用新的Magento 2编号分配规则。 新销售实体的数字不同。

## 步骤

### 仅重新保存客户区段[Adobe Commerce]

迁移后，必须从管理面板中重新保存客户区段才能使其启动并运行。

### 配置时区

该工具不迁移时区设置，因此您必须在迁移后在&#x200B;**商店** > **配置** > **区域设置选项** > **时区**&#x200B;手动配置时区。

默认情况下，Magento在数据库的UTC-0区域中存储时间数据，并根据当前时区设置显示这些数据。 如果时间数据已保存在数据库的UTC-0以外的区域中，则必须使用[!DNL Data Migration Tool]的`\Migration\Handler\Timezone`处理程序将现有时间转换为UTC-0。

在以下示例中，Magento 1在数据库的UTC-7区域中错误地节省了时间（例如，由于第三方扩展出错）。 要在迁移时将客户帐户创建时间正确转换为UTC-0区域，请执行以下步骤：

1. 将`map-customer.xml.dist`配置文件从[!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`)的相应目录复制到`<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml`文件中。

1. 更新`<customer_map_file>`中的`config.xml`节点并从`.dist`中删除`map-customer.xml.dist`扩展

1. 将以下规则添加到`map-customer.xml`文件：

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
