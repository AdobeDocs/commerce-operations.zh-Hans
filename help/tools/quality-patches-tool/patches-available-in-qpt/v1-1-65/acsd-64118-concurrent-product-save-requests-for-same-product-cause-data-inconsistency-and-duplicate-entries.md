---
title: ACSD-64118：对同一产品的并发产品保存请求会导致数据不一致和重复条目
description: 应用ACSD-64118修补程序以修复Adobe Commerce问题，该问题导致同时请求保存和更新同一产品导致数据不一致或产品重复。
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: e014645e-72b2-4b3d-8b44-3daca502c950
source-git-commit: 5c84dc5c27f6e57b4116bc1a3d4fb001b55b63f1
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-64118：对同一产品的并发产品保存请求会导致数据不一致和重复条目

ACSD-64118修补程序修复了以下问题：保存和更新同一产品的并发请求导致数据不一致或产品重复。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65时，此修补程序可用。 修补程序ID为ACSD-64118。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p7

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

同时请求保存和更新同一产品会导致数据不一致或产品重复。

<u>重现步骤</u>：

1. 在`env.php`中为使用者设置多进程：

   ```
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. 向主网站添加其他商店和新商店。
1. 使用下列有效负载将批量API请求发送到默认的storeview端点`/rest/default/async/bulk/V1/products`以创建产品：

   ```
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. 使用相同有效负载将批量API请求发送到新的storeview端点`/rest/store/async/bulk/V1/products`以更新产品。
1. 刷新缓存。
1. 运行cron作业。
1. 检查`catalog_product_entity`表中前面的步骤中产品的条目。

<u>预期的结果</u>：

* `catalog_product_entity`表中应存在产品SKU的单个条目。
* 第一个REST API请求应创建一个数据库条目，所有后续请求都应更新该数据库条目。

<u>实际结果</u>：

`catalog_product_entity`表中存在同一SKU的多个条目。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
