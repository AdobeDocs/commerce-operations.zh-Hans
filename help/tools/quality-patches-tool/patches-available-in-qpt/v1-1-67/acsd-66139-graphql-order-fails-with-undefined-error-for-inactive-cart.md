---
title: ACSD-66139：对于不活动的购物车，GraphQL订单失败并出现“未定义”错误
description: 应用ACSD-66139修补程序以修复Adobe Commerce问题：在对不存在或不活动的购物车下订单时，GraphQL在翻译错误消息时返回“未定义”错误代码而不是特定的错误代码。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 16d95ae0d58dfdc88a5fab725a37d353d3ee5c96
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# ACSD-66139：对于不活动的购物车，GraphQL订单失败并出现“UNDEFINED”错误

ACSD-66139修补程序修复了以下问题：当对不存在或不活动的购物车下订单时，GraphQL在翻译错误消息时返回&#x200B;*UNDEFINED*&#x200B;错误代码，而不是特定的错误代码。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67时，此修补程序可用。 修补程序ID为ACSD-66139。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果转换了错误消息，GraphQL在为不存在或不活动的购物车下订单时返回&#x200B;*UNDEFINED*&#x200B;错误代码，而不是特定错误代码。

<u>重现步骤</u>：

1. 添加`app/i18n/Magento/de_DE/de_DE.csv`并包含以下错误字符串转换：

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. 在“管理员”面板中创建商店视图。 转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**。 单击&#x200B;**[!UICONTROL Create Store View]**，对于&#x200B;**[!UICONTROL Code]**，输入代码`test`。
1. 将`german`语言分配给新创建的商店视图。
1. 运行`setup:upgrade`和`setup:static-content:deploy -f`。
1. 使用标头“Store:test”运行以下GraphQL查询：

```
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u>预期的结果</u>：

更正错误响应：

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "CART_NOT_FOUND"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

<u>实际结果</u>：

返回的`error_code`是&#x200B;*未定义*：

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "UNDEFINED"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
