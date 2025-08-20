---
title: ACSD-57477：销售规则处理会降低购物车相关请求的性能
description: 应用ACSD-57477修补程序以修复Adobe Commerce问题：在具有许多可用产品属性（例如，1000个属性）的项目中，当使用变量执行AddProductsToCart GraphQL操作时，Commerce会尝试加载所有这些产品属性，并导致AddProductsToCart GraphQL操作出现性能缓慢问题。
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 00fce49fbe5432a16324937e0430a08ec7c41188
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-57477：销售规则处理会降低购物车相关请求的性能

ACSD-57477修补程序修复了销售规则处理导致与购物车相关的请求性能缓慢的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-57477。 请注意，此问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果将参数作为GraphQL变量发送，则销售规则处理会导致与购物车相关的请求性能缓慢。

<u>重现步骤</u>：

1. 添加1000个产品属性。
1. 使用以下GraphQL查询创建购物车。

   ```
   mutation {createEmptyCart}{noformat}
   ```

1. 使用以下GraphQL查询将产品添加到购物车。

   ```
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. 设置这些变量。

   ```
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. 仅当您作为GraphQL变量发送参数时，才会发生此问题。 如果将参数包含到GraphQL查询本身中，则不会出现此问题。
1. 向GraphQL查询本身添加参数后，发送相同的&#x200B;**添加到购物车**&#x200B;请求。

   ```
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u>预期的结果</u>：

不应降低`AddProductsToCart` GraphQL操作性能。

<u>实际结果</u>：

`AddProductsToCart` GraphQL操作性能下降，因为它在参数作为变量发送时加载所有产品属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： Tools指南中用于优质修补程序的Self-service工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
