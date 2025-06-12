---
title: ACSD-57846：使用零价格过滤器搜索的GraphQL产品未返回结果
description: 应用ACSD-57846修补程序以修复Adobe Commerce问题，该问题导致从零开始筛选产品会导致向 [!DNL OpenSearch] 发出格式错误的请求，并且不会返回任何结果。
feature: GraphQL, Products
role: Admin, Developer
exl-id: ec523a54-201b-4a8f-85ce-cbe1d0bf1304
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-57846：使用零价格过滤器搜索的GraphQL产品未返回结果

ACSD-57846修补程序修复了以下问题：按零价格筛选产品会导致向[!DNL OpenSearch]发出格式错误的请求，并且不会返回任何结果。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49时，此修补程序可用。 修补程序ID为ACSD-57846。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在GraphQL产品搜索中以零价格筛选产品会导致对[!DNL OpenSearch]的请求格式不正确，并且不会返回任何结果。

<u>重现步骤</u>：

1. 创建包含两个简单产品的类别：
   * 简单1 — 价格$0
   * 简单2 — 价格$10
1. 确保这两种产品在前端可见。
1. 使用`price:{from:"1"}`发送请求。

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"1"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

1. 这会返回产品&#x200B;*simple2*。
1. 现在使用`price:{from:"0"}`发送请求。

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"0"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

<u>预期的结果</u>：

同时返回产品&#x200B;*simple1*&#x200B;和&#x200B;*simple2*。

<u>实际结果</u>：

不返回任何产品。

```json
{
    "data": {
        "products": {
            "totalResult": 0,
            "productItems": []
        }
    }
}
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
