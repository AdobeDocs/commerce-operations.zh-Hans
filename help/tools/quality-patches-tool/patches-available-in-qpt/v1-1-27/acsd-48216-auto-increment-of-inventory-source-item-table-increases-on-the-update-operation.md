---
title: ACSD-48216： *INVENTORY_source_item*表的AUTO_INCREMENT在*UPDATE*操作时增加
description: 应用ACSD-48216修补程序以修复Adobe Commerce问题，该问题导致inventory_source_item*表的*AUTO_INCREMENT在*UPDATE*操作时增加。
feature: Admin Workspace, Inventory, Orders
role: Admin
exl-id: acb956c8-75d4-4764-8b8d-250bc8620b29
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-48216： *UPDATE*&#x200B;操作时&#x200B;*inventory_source_item*&#x200B;表的&#x200B;*AUTO_INCREMENT*&#x200B;增加

ACSD-48216修补程序修复了&#x200B;*inventory_source_item*&#x200B;表的&#x200B;*AUTO_INCREMENT*&#x200B;在&#x200B;*UPDATE*&#x200B;操作中增加的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27时，此修补程序可用。 修补程序ID为ACSD-48216。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`inventory_source_item`表的`AUTO_INCREMENT`在`UPDATE`操作中增加。

<u>重现步骤</u>：

1. 检查`inventory_source_item`表的`AUTO_INCREMENT`的当前值：

```bash
MySQL > show create table inventory_source_item;
```

```SQL
CREATE TABLE `inventory_source_item` (
  `source_item_id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `source_code` varchar(255) NOT NULL,
  `sku` varchar(64) NOT NULL,
  `quantity` decimal(12,4) NOT NULL DEFAULT '0.0000',
  `status` smallint(5) unsigned NOT NULL DEFAULT '0',
  PRIMARY KEY (`source_item_id`),
  UNIQUE KEY `INVENTORY_SOURCE_ITEM_SOURCE_CODE_SKU` (`source_code`,`sku`),
  KEY `INVENTORY_SOURCE_ITEM_SKU_SOURCE_CODE_QUANTITY` (`sku`,`source_code`,`quantity`),
  CONSTRAINT `INVENTORY_SOURCE_ITEM_SOURCE_CODE_INVENTORY_SOURCE_SOURCE_CODE` FOREIGN KEY (`source_code`) REFERENCES `inventory_source` (`source_code`) ON DELETE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=2048 DEFAULT CHARSET=utf8
```

1. 为特定产品发出API请求：

`Endpoint: /rest/V1/inventory/source-items`\
`Method: POST`\
`Headers: Authorization: Bearer <admin_token>`

有效负载：

```JSON
{
    "sourceItems": [
        {
            "sku": "24-MB01",
            "source_code": "default",
            "quantity": 200,
            "status": 1
        }
    ]
}
```

1. 再次检查`inventory_source_item`表的`AUTO_INCREMENT`值。

<u>预期的结果</u>：

在每次更新操作后，`inventory_source_item`表的`AUTO_INCREMENT`值不会增加。

<u>实际结果</u>：

每次更新操作后，`inventory_source_item`表的`AUTO_INCREMENT`值都会增加。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相关阅读

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
