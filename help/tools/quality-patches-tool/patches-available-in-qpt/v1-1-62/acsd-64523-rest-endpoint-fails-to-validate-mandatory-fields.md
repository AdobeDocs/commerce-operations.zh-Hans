---
title: ACSD-64523：REST端点无法验证必填字段
description: 应用ACSD-64523修补程序以修复REST端点“[V1/import/csv]”无法验证必填字段的问题，从而允许在不提供必填字段的情况下创建产品。
feature: REST, Products, Admin Workspace
role: Admin, Developer
source-git-commit: 4bf9a5eb2e423f5981ee9234be57230a6dff3913
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# ACSD-64523：REST端点无法验证必填字段

ACSD-64523修补程序修复了REST端点[V1/import/csv]无法验证必填字段的问题，从而允许在没有必需数据的情况下创建产品。 要解决此问题，请更新Authorization标头。安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62时，此修补程序可用。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

REST端点`[V1/import/csv]`无法验证必填字段，允许创建产品而不提供这些必填字段。

<u>重现步骤</u>：

1. 执行以下有效负载（更新授权标头）：

   ```
   curl --location 'http://<domain>/rest/default/V1/import/json' \
   --header 'Content-Type: application/json' \
   --header 'Authorization: Bearer xxxxx' \
   --data '{
       "source": {
           "locale": "en_AU",
           "entity": "catalog_product",
           "behavior": "append",
           "validation_strategy": "validation-stop-on-errors",
           "allowed_error_count": 0,
           "items": [
               {
                   "sku": "product_sku",
                   "product_online": "no",
                   "attribute_set_code": "Default",
                   "product_type": "configurable",
                   "product_websites": "base",
                   "store_view_code": "default",
                   "name": null,
                   "description": null,
                   "short_description": null,
                   "weight": null,
                   "tax_class_name": null,
                   "visibility": null,
                   "price": null,
                   "url_key": null,
                   "cost": null,
                   "additional_attributes": {
                       "special_price": "",
                       "retail_price": ""
                   },
                   "configurable_variations": []
               }
           ]
       }
   }'
   ```

<u>预期的结果</u>：

该应用程序应阻止保存没有必填字段的产品。

<u>实际结果</u>：

产品已成功保存，但未指定产品名称（必需属性）。 因此，我们无法访问后端产品网格，并出现以下错误。

`Warning: Undefined array key "name" in /app/code/Magento/Catalog/Ui/Component/Listing/Columns/Thumbnail.php on line 91`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
