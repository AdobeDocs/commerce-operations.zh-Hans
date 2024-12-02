---
title: ACSD-47292：GraphQL响应中没有现成的捆绑产品
description: Adobe Commerce应用ACSD-47292修补程序以修复以下问题：即使“显示缺货产品”设置为“是”，GraphQL响应中仍无法使用缺货捆绑产品。
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
exl-id: 3b8114a3-cc45-4d65-af74-cb3e905d7f75
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-47292：GraphQL响应中没有现成的捆绑产品

ACSD-47292修补程序修复了即使[!UICONTROL Display Out-of-Stock Products]设置为&#x200B;*[!UICONTROL Yes]*，GraphQL响应中也不可用的缺货捆绑产品的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25时，此修补程序可用。 修补程序ID为ACSD-47292。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

缺货捆绑产品在GraphQL响应中不可用，即使[!UICONTROL Display Out-of-Stock Products]设置为&#x200B;*[!UICONTROL Yes]*&#x200B;也是如此。

<u>重现步骤</u>：

1. 转到Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**，并将[!UICONTROL Display Out-of-Stock Products]设置为&#x200B;*[!UICONTROL Yes]*。
1. 创建两个简单的产品s1和s2。
1. 使s1缺货且单独不可见，使s2缺货且单独不可见，并将它们分配给某个类别。
1. 创建至少包含一个选项产品的捆绑产品，并将s1和s2分配给此选项（输入类型“RadioButton”）。
1. 保存捆绑的产品并将其分配给类别。
1. 转到店面并打开此捆绑产品。 您会看到缺货选项s1呈灰色但可见。
1. 发送GraphQL请求：

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>预期的结果</u>：

s1捆绑包选项在GraphQL响应中列出，因为[!UICONTROL Display Out-of-Stock Products]设置为&#x200B;*[!UICONTROL Yes]*，并且在店面中可见。

<u>实际结果</u>：

GraphQL响应中未列出s1捆绑包选项。

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
