---
title: MDVA-39521：无法通过GraphQL设置购物车上的配送地址
description: MDVA-39521修补程序解决了用户无法通过GraphQL为电话号码为空的购物车设置送货地址的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39521。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: GraphQL, Orders, Shipping/Delivery, Shopping Cart
role: Admin
exl-id: aac44c20-b244-472b-bab0-7d6e7d99608a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39521：无法通过GraphQL设置购物车上的配送地址

MDVA-39521修补程序解决了用户无法通过GraphQL为电话号码为空的购物车设置送货地址的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39521。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户无法通过GraphQL为电话号码为空的购物车设置送货地址，尽管Show Telephone配置为可选。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 转到&#x200B;**商店** > **配置** > **客户** > **客户配置** > **名称和地址选项**，并将“显示电话”设置为可选。
1. 通过GraphQL请求创建一个空购物车。

   ```GraphQL
   mutation {
   createEmptyCart
   }
   ```

1. 将产品添加到购物车。

   ```GraphQL
   mutation {
   addSimpleProductsToCart(
   input: {
     cart_id: "{ CART_ID }"
     cart_items: [
       {
         data: {
           quantity: 1
           sku: "24-MG04"
         }
       }
     ]
   }
   ) {
   cart {
     items {
       id
       product {
         sku
         stock_status
       }
       quantity
     }
   }
   }
   }
   ```

1. 添加地址：GRAPHQL变量。

   ```GraphQL
   {
     "cartId": "6Efw00UbjPoP5cvTFhsswDTjpxs0Xupt"
   }
   ```

   ```GraphQL
   mutation ($cartId: String!) {
     setShippingAddressesOnCart(input: {cart_id: $cartId, shipping_addresses:
     {address: {firstname: "John", lastname: "Doe", company: "Company Name",
     street: ["820 Burrard Street"], city: "Vancouver", region: "BC", postcode: "V6Z 2J1",
     country_code: "CA", telephone: "123-456-0000", save_in_address_book: false}}}) {
       cart {
         shipping_addresses {
           firstname
           lastname
           company
           street
           city
           postcode
           telephone
           country {
             code
             label
           }
         }
       }
     }
   }
   ```

   结果：

   ```GraphQL
     {
         "data": {
             "setShippingAddressesOnCart": {
                 "cart": {
                     "shipping_addresses": [
                         {
                             "firstname": "John",
                             "lastname": "Canada",
                             "company": "Company Name",
                             "street": [
                                 "820 Burrard Street"
                             ],
                             "city": "Vancouver",
                             "postcode": "V6Z 2J1",
                             "telephone": "123-456-0000",
                             "country": {
                                 "code": "CA",
                                 "label": "CA"
                             }
                         }
                     ]
                 }
             }
         }
     }
   ```

1. 添加电话号码为空的地址。

   ```GraphQL
   mutation ($cartId: String!) {
     setShippingAddressesOnCart(input: {cart_id: $cartId, shipping_addresses: {address: {firstname:
       "John", lastname: "Canada", company: "Company Name", street: ["820 Burrard Street"], city:
       "Vancouver", region: "BC", postcode: "V6Z 2J1", country_code: "CA", telephone: "123-456-0000",
       save_in_address_book: false}}}) {
       cart {
         shipping_addresses {
           firstname
           lastname
           company
           street
           city
           postcode
           telephone
           country {
             code
             label
           }
         }
       }
     }
   }
   ```

<u>预期的结果</u>：

```GraphQL
 {
    "data": {
        "setShippingAddressesOnCart": {
            "cart": {
                "shipping_addresses": [
                    {
                        "firstname": "John",
                        "lastname": "Doe",
                        "company": "Company Name",
                        "street": [
                            "820 Burrard Street"
                        ],
                        "city": "Vancouver",
                        "postcode": "V6Z 2J1",
                        "telephone": "",
                        "country": {
                            "code": "CA",
                            "label": "CA"
                        }
                    }
                ]
            }
        }
    }
 }
```

<u>实际结果</u>：

```GraphQL
{
    "data": {
        "setShippingAddressesOnCart": {
            "cart": {
                "shipping_addresses": []
            }
        }
    }
}
```

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查是否有可用于Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT[中可用的](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)修补程序部分。
