---
title: ACSD-60538：如果在[!UICONTROL All Store Views]中禁用了产品，则属性无法正确显示
description: 应用ACSD-60538修补程序以修复Adobe Commerce问题：如果某个产品在*所有商店视图*中处于禁用状态，并且只在特定商店视图范围内处于启用状态，则产品属性在GraphQL响应中无法正确显示，从而导致产品无法正确显示。
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538：如果在&#x200B;*[!UICONTROL All Store Views]*&#x200B;中禁用了产品，则属性无法正确显示

ACSD-60538修补程序修复了以下问题：如果某个产品在&#x200B;*[!UICONTROL All Store Views]*&#x200B;中处于禁用状态，并且只在特定商店视图范围内启用，则产品属性在GraphQL响应中无法正确显示，从而导致产品无法正确显示。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51时，此修补程序可用。 修补程序ID为ACSD-60538。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果在&#x200B;*[!UICONTROL All Store Views]*&#x200B;中禁用了某个产品，并且只在特定商店视图范围内启用了某个产品，则产品属性在GraphQL响应中无法正确显示，从而导致产品无法正确显示。

<u>先决条件</u>：

清单模块已安装。

<u>重现步骤</u>：

1. 创建具有&#x200B;*color*&#x200B;属性和三个子产品（*blue*、*black*&#x200B;和&#x200B;*brown*）的可配置产品。
1. 在&#x200B;*[!UICONTROL All Store Views]*&#x200B;作用域上禁用两个关联的子产品（*blue*&#x200B;和&#x200B;*black*）。
1. 转到&#x200B;**[!UICONTROL Store View]**&#x200B;范围。
1. 在&#x200B;*[!UICONTROL Store View]*&#x200B;作用域上启用子产品（*blue*&#x200B;和&#x200B;*black*）。
1. 运行以下GraphQL请求：

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
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

GraphQL响应包含在&#x200B;*[!UICONTROL All Store Views]*&#x200B;上禁用并在&#x200B;*[!UICONTROL Store View]*&#x200B;范围上启用的子关联产品的属性值。

<u>实际结果</u>：

在&#x200B;*[!UICONTROL All Store Views]*&#x200B;上禁用并在&#x200B;*[!UICONTROL Store View]*&#x200B;范围中启用子关联产品时，GraphQL响应的属性值为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
