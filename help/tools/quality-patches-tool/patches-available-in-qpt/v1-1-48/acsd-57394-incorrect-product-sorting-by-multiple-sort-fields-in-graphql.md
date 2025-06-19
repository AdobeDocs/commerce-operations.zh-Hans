---
title: ACSD-57394： [!DNL GraphQL]中按多个排序属性排序的产品排序不正确
description: 应用ACSD-57394修补程序以修复在 [!DNL GraphQL]中使用多个排序属性时产品排序不正确的Adobe Commerce问题。
feature: GraphQL, Products
role: Admin, Developer
exl-id: 3e4ca535-37ed-4363-ba6c-968eb53b98b3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-57394： [!DNL GraphQL]中按多个排序属性排序的产品排序不正确

ACSD-57394修补程序修复了在[!DNL GraphQL]中使用多个排序属性时产品排序不正确的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48时，此修补程序可用。 修补程序ID为ACSD-57394。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在[!DNL GraphQL]中使用多个排序属性时，产品排序不正确。

<u>重现步骤</u>：

1. 创建几个具有不同价格和名称的产品。
1. 创建一个类别并将创建的产品分配给该类别。
1. 为具有几个&#x200B;*排序*&#x200B;属性的已创建类别发送[!DNL GraphQL]产品查询。 例如：

   ```
   {
   products(
     currentPage: 1
     pageSize: 10
     filter: {
       category_id: {
         eq :"3"
       }
     }
     sort: {  price: DESC, name: ASC, position: ASC
     }
   ){
   items{
     name
     sku
   
       price_range {
           minimum_price {
   
         regular_price {
           value
           currency
         }
         final_price {
           value
           currency
         }
         discount {
           amount_off
           percent_off
         }
               }
           }
      }
     }
    }
   ```

1. 创建&#x200B;*sort*&#x200B;属性后检查响应。

<u>预期的结果</u>：

退货的顺序应该正确。 按多个属性对产品进行排序应该有效。

<u>实际结果</u>：

产品未按正确顺序退回。 无法按多个属性对产品进行排序。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
