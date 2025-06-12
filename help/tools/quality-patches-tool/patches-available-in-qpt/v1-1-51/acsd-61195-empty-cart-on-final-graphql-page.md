---
title: ACSD-61195：购物车GraphQL请求无法返回最终页面上的项目
description: 应用ACSD-61195修补程序以修复在购物车GraphQL请求的最后一页上未返回购物车项目的Adobe Commerce问题。
feature: GraphQL
role: Admin, Developer
exl-id: 15f0f29c-8517-4f1e-9370-772572e75c9a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ACSD-61195：购物车GraphQL请求无法返回最终页面上的项目

ACSD-61195修补程序修复了在购物车GraphQL请求的最后一页未返回购物车项目的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.51时，此修补程序可用。 修补程序ID为ACSD-61195。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7-p1 - 2.4.7-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

购物车GraphQL请求无法在最终页面上返回项目。

<u>重现步骤</u>：

1. 创建新购物车：

   ```
   mutation createEmptyCart($input: createEmptyCartInput) {
       createEmptyCart(input: $input)
   } 
   ```

1. 将五个以上的产品添加到购物车：

   ```
   addProductsToCart(
       cartId: "{{cartId}}"
       cartItems: [
         {
           quantity: 1
           sku: "test"
         }
       ]
     ) {
       cart {
          itemsV2 {
          items {
           product {
            name
            sku
           }
           quantity
       }
       total_count
       page_info {
         page_size
         current_page
         total_pages
       }
     }
   }
   user_errors {
     code
     message
   }
   }
   }
   ```

1. 运行以下查询：

   ```
   cart(cart_id: $cartId) {
   email
   itemsV2(pageSize: 2, currentPage: 3) {
       total_count
       page_info {
          page_size
          current_page
          total_pages
       }
     items {
       id
       product {
         name
         sku
       }
       quantity
       }
   }
   }  
   ```

<u>预期的结果</u>：

查询返回最后一页上的项目。

<u>实际结果</u>：

```
  {
    "data": {
        "cart": {
            "email": "roni_cost@example.com",
            "itemsV2": {
                "total_count": 5,
                "page_info": {
                    "page_size": 2,
                    "current_page": 3,
                    "total_pages": 3
                },
                "items": []
            }
        }
    } 
    }  
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
