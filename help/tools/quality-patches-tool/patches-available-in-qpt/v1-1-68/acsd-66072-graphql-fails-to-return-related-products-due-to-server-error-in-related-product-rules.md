---
title: ACSD-66072：GraphQL无法在“产品详细信息”页面上返回相关产品
description: 应用ACSD-66072补丁以修复在配置相关产品规则时由于内部服务器错误导致产品详细信息页面上无法通过GraphQL返回相关产品的Adobe Commerce问题。
feature: GraphQL, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: b1cd5383d774ab0ed97b80a4abf7df5706706ea5
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66072：GraphQL无法在“产品详细信息”页面上返回相关产品

ACSD-66072修补程序修复了在配置&#x200B;**[!UICONTROL Related Products Rule]**&#x200B;时由于内部服务器错误而导致相关产品无法通过GraphQL在产品详细信息页面上返回的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-66072。 请注意，该问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于配置&#x200B;**[!UICONTROL Related Products Rule]**&#x200B;时出现内部服务器错误，相关产品不会通过“产品详细信息”页面上的GraphQL返回。

<u>重现步骤</u>：

1. 创建可配置产品：
   * **产品1**： `config1`带`option1`
   * **产品2**： `config2`带`option2`

1. 创建产品并将其分配给类别
   * 创建&#x200B;**新类别**。
   * 将两个产品（`config1`和`config2`）分配给此类别。

1. 导航到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Related Products Rule]**，然后使用以下设置创建新规则：

   * **[!UICONTROL Priority]**： 1
   * **[!UICONTROL Applies To]**： **[!UICONTROL Related Products]**
   * **[!UICONTROL Result Limit]**： 10
   * **[!UICONTROL Products to Match]**： **[!UICONTROL Attribute Set is Default]**
   * **[!UICONTROL Products to Display]**： `Product Category is the Same as Matched Product Categories`

1. 运行以下Magento CLI命令：

   ```bash
   bin/magento indexer:reindex
   bin/magento cache:clean
   ```

1. 使用以下有效负载向`../graphql`发送POST请求：

   ```
   query getRelatedProductsForProductPage($urlKey: String!) 
   {
       products(filter: { url_key: { eq: $urlKey } }) 
       {
           items {
               id
               __typename
               uid
               url_key
               name
               sku
               related_products {
                   id
                   uid
                   name
                   sku
                   stock_status
                   url_key
                   small_image {
                       url
                       __typename
                       }
                       thumbnail {
                           url
                           __typename
                           }
                           image {
                               url
                               __typename
                               }
                               price_range {
                                   maximum_price {
                                       regular_price {
                                           currency
                                           value
                                           __typename
                                           }
                                           __typename
                                           }
                                           minimum_price {
                                               discount {
                                                   amount_off
                                                   percent_off
                                                   __typename
                                                   }
                                                   final_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       regular_price {
                                                           currency
                                                           value
                                                           __typename}
                                                           __typename}
                                                           __typename}
                                                           __typename
                                                           }
                                                           }
                                                           __typename
                                                           }
                                                           }
   ```

<u>预期的结果</u>：

查询返回相关产品(`config1`)。

<u>实际结果</u>：

```graphql
{
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 10,
                    "column": 7
                }
            ],
            "path": [
                "products",
                "items",
                0,
                "related_products"
            ]
        }
    ],
    "data": {
        "products": {
            "items": [
                {
                    "id": 4,
                    "__typename": "ConfigurableProduct",
                    "uid": "NA==",
                    "url_key": "config2",
                    "name": "config2",
                    "sku": "config2",
                    "related_products": null
                }
            ],
            "__typename": "Products"
        }
    }
}
```

`var/log/exception.log`文件包含：

```
report.ERROR: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in /home/magento2ee/app/code/Magento/TargetRule/Model/ResourceModel/Index.php on line 557
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
