---
title: 'MDVA-43348：礼品卡GraphQL请求显示错误'
description: MDVA-43348修补程序修复了礼品卡GraphQL请求在“gift_card_options”包含“uid”时显示错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43348。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Gift, GraphQL
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# MDVA-43348：礼品卡GraphQL请求显示错误

MDVA-43348修补程序修复了礼品卡GraphQL请求在`gift_card_options`包含“uid”时显示错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43348。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果gift_card_options中包含“uid”，礼品卡GraphQL请求会显示错误。

<u>重现步骤</u>：

1. 创建礼品卡产品。
1. 执行重新索引。
1. 进行GraphQL调用，其中URL键为“礼品卡”：

<pre>
<code class="language-graphql">
query getProductOptionsForProductPage_bypassFastly($urlKey: String!) {
  products(filter: { url_key: { eq: $urlKey } }) {
    items {
      id
      url_key
      ... on GiftCardProduct {
        allow_open_amount
        open_amount_min
        open_amount_max
        giftcard_type
        is_redeemable
        lifetime
        allow_message
        message_max_length
        gift_card_options {
          uid
          title
          required
        }
      }
    }
  }
}
</code>
</pre>

<u>预期的结果</u>：

礼品卡数据会根据请求返回。

<u>实际结果</u>：

在请求礼品卡数据时出现以下错误：

<pre>
<code class="language-graphql">
{
  "errors": [
    {
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 16,
          "column": 1
        }
      ],
      "path": [
        "products",
        "items",
        0,
        "gift_card_options",
        0,
        "uid"
      ]
    },
    {
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 16,
          "column": 1
        }
      ],
      "path": [
        "products",
        "items",
        0,
        "gift_card_options",
        1,
        "uid"
      ]
    },
    {
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 16,
          "column": 1
        }
      ],
      "path": [
        "products",
        "items",
        0,
        "gift_card_options",
        2,
        "uid"
      ]
    },
    {
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 16,
          "column": 1
        }
      ],
      "path": [
        "products",
        "items",
        0,
        "gift_card_options",
        3,
        "uid"
      ]
    },
    {
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 16,
          "column": 1
        }
      ],
      "path": [
        "products",
        "items",
        0,
        "gift_card_options",
        4,
        "uid"
      ]
    }
  ],
  "data": {
    "products": {
      "items": [
        {
          "id": 2,
          "url_key": "gitf-card",
          "allow_open_amount": false,
          "open_amount_min": null,
          "open_amount_max": null,
          "giftcard_type": "VIRTUAL",
          "is_redeemable": true,
          "lifetime": 0,
          "allow_message": true,
          "message_max_length": 255,
          "gift_card_options": [
            null,
            null,
            null,
            null,
            null
          ]
        }
      ]
    }
  }
}
</code>
</pre>

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
