---
title: ACSD-45817：GraphQL产品突变会提供所有可配置变体
description: ACSD-45817修补程序修复了以下问题：特定存储的GraphQL“products”突变会返回所有可配置变体，包括那些未分配给所请求存储的变体。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18后，即可使用此修补程序。 修补程序ID为ACSD-45817。 请注意，Adobe Commerce 2.4.4中已修复此问题。
feature: GraphQL, Configuration, Products
role: Admin
exl-id: f00e9a8e-c18b-4fa8-b7c6-c228b6a22a2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-45817：GraphQL产品突变会提供所有可配置变体

ACSD-45817修补程序修复了以下问题：特定存储的GraphQL `products`突变返回所有可配置变体，包括那些未分配给所请求存储的变体。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18时，此修补程序可用。 修补程序ID为ACSD-45817。 请注意，Adobe Commerce 2.4.4中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

特定存储的GraphQL `products`突变会返回所有可配置的变体，包括那些未分配给所请求存储的变体。

<u>先决条件</u>：

创建第2个网站、第2个商店和第2个商店视图。

<u>重现步骤</u>：

1. 创建包含两个子产品的可配置产品：“configurable-a”和“configurable-b”。
1. 将可配置产品分配给两个网站。
1. 仅向第二个网站分配一个“可配置 — a”变体。
1. 转到&#x200B;**店面**，切换到第二个网站，然后打开可配置的产品。
1. 确保只看到一个子选项：&quot;configurable-a&quot;。
1. 使用`POST: /graphql`终结点和`Headers: "store" = "new"`运行GraphQL查询

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>预期的结果</u>：

“configurable-b”变体未分配给第2个网站，因此不应显示在响应中。

<u>实际结果</u>：

响应中显示“configurable-b”变量。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
