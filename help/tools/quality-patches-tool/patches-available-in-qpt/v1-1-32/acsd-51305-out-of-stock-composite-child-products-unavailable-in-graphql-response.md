---
title: ACSD-51305：GraphQL响应中不可用的缺货复合子产品
description: 应用ACSD-51305修补程序以修复缺货的复合子产品在Adobe Commerce响应中不可用的GraphQL问题。
feature: Categories, GraphQL, Orders, Products
role: Admin
exl-id: 110bb332-2032-4aaf-b95e-971fc3382262
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51305：GraphQL响应中不可用的缺货复合子产品

ACSD-51305修补程序修复了GraphQL响应中无现成复合子产品可用的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32时，此修补程序可用。 修补程序ID为ACSD-51305。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL响应中没有现成的复合子产品。

<u>重现步骤</u>：

1. 登录到Admin网站。
1. 创建类别(cat1， id=3)。
1. 创建&#x200B;*simple1*&#x200B;产品（缺货，不可单独显示，已分配给&#x200B;*cat1*）。
1. 创建一个&#x200B;*simple2*&#x200B;产品（有库存，不单独显示，已分配给&#x200B;*cat1*）。
1. 创建包含&#x200B;*simple1*&#x200B;和&#x200B;*simple2*&#x200B;子产品的&#x200B;*捆绑包1*&#x200B;产品作为单选按钮&#x200B;*option1*&#x200B;产品，并将其分配给&#x200B;*cat1*&#x200B;类别。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**。

   * 将&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;设置为&#x200B;*是*。

1. 打开店面上的&#x200B;*bundle1*&#x200B;产品，并确保其中同时显示&#x200B;*simple1*&#x200B;和&#x200B;*simple2*&#x200B;子产品。
1. 运行以下GraphQL查询：

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

**[!UICONTROL Options]**&#x200B;块中的&#x200B;**[!UICONTROL Product]**&#x200B;节不为空。

<u>实际结果</u>：

**[!UICONTROL Options]**&#x200B;块中的&#x200B;**[!UICONTROL Product]**&#x200B;节为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
