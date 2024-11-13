---
title: “ACSD-60684： [!DNL GraphQL] 按多个字段排序的产品无法按预期工作”
description: 应用ACSD-60684修补程序以修复在变量中传递排序时，按多个字段对 [!DNL GraphQL] 产品进行排序不起作用的Adobe Commerce问题。
feature: GraphQL, Products, Search
role: Admin, Developer
source-git-commit: 279036e9e7247ce915820a4b00173644ee7252b1
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-60684：按多个字段排序的[!DNL GraphQL]产品无法按预期使用

ACSD-60684修补程序修复了在变量中传递排序时[!DNL GraphQL]产品按多个字段排序不起作用的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52时，此修补程序可用。 修补程序ID为ACSD-60684。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

按多个字段排序的[!DNL GraphQL]产品无法按预期使用。

<u>重现步骤</u>：

1. 创建三个名为A、B和C的产品。
1. 使用以下[!DNL GraphQL]获取产品：

   ```
   query FindProducts($search: String, $filter:ProductAttributeFilterInput!, $pageSize: Int!, $currentPage: Int!, $sort: ProductAttributeSortInput!){
       products(search: $search, filter: $filter, pageSize: $pageSize, currentPage: $currentPage, sort: $sort){
           total_count
           page_info{total_pages}
           items{
               __typename
               url_key
               sku
               name
               stock_status
               price_range{
                   minimum_price{
                       final_price{
                           value
                           currency
                       }
                   }
               }
           }
       }
   } 
   ```

   变量：

   ```
   {
       "search": null,
       "filter": {
   
       },
       "pageSize": 24,
       "currentPage": 1,
       "sort": {
           "name": "ASC"
       }
   }  
   ```

1. 使用`sort`重复查询： `DESC`

<u>预期的结果</u>：

对结果进行了适当的排序。

<u>实际结果</u>：

尚未应用已选择的排序。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
