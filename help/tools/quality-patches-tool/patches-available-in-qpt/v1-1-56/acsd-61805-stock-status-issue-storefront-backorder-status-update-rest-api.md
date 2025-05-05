---
title: ACSD-61805：修复了通过REST API更新延交状态后的店面库存问题
description: 应用ACSD-61805补丁以修复通过REST API更新延交订单状态后店面产品缺货的Adobe Commerce问题
feature: REST, Catalog Management, Inventory
role: Admin, Developer
source-git-commit: abad1a2f2a1bdc2c1a4b6f821e6b02190a5ebe83
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-61805：修复了通过REST API更新延交状态后的店面库存问题

ACSD-61805修补程序修复了在通过REST API更新延交订单状态后，产品在店面中保持缺货状态的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56时，此修补程序可用。 修补程序ID为ACSD-61805。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过REST API更新延交状态后，店面上的产品保持缺货。

<u>重现步骤</u>：

1. 安装包含示例数据的干净实例。
1. 创建新的库存来源。
1. 创建新的库存库存并为其分配新来源。
1. 将新源分配给产品24-MB01。
1. 将两个产品源的&#x200B;**[!UICONTROL Source Item Status]**&#x200B;设置为`In Stock`。
1. 将两个产品数量的数量(**[!UICONTROL QTY]**)设置为&#x200B;*0*。
1. 保存产品。
1. 从此终结点URL获取管理令牌： `/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. 使用终结点更新产品： `/rest/default/V1/products`

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. 运行cron作业两次（一次用于创建计划，一次用于运行计划）：

   ```bash
   bin/magento cron:run
   ```

1. 前往前端并检查产品。

<u>预期的结果</u>：

产品应为&#x200B;*库存*。

<u>实际结果</u>：

产品缺货&#x200B;**。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
