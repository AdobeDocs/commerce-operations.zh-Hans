---
title: MDVA-37234：将项目多次添加到购物车会创建重复的行项目
description: MDVA-37234修补程序修复了以下问题：对于同一SKU，将项目多次添加到购物车（并行请求），会为同一购物车ID创建一个重复的行项目。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3后，即可使用此修补程序。 修补程序ID为MDVA-37234。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Orders, Shopping Cart
role: Admin
exl-id: d4e9fca1-7fba-4a33-9c5e-c9695cbfc61c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-37234：将项目多次添加到购物车会创建重复的行项目

MDVA-37234修补程序修复了以下问题：对于同一SKU，将项目多次添加到购物车（并行请求），会为同一购物车ID创建一个重复的行项目。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3时，此修补程序可用。 修补程序ID为MDVA-37234。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.3.6、2.4.1和2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.5 - 2.3.7-p1和2.4.1 - 2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将同一SKU的项目多次添加到购物车（并行请求）会为同一购物车ID创建一个重复的行项目。

<u>重现步骤</u>：

1. 使用SKU = simple1创建一个简单的产品。
1. 创建客户。
1. 生成用于发出GraphQL请求的客户令牌。

   <pre>
    <code class="language-graphql">
    mutation {
        generateCustomerToken(
            email: "customer email"
            password: "customer password"
        )
        {
            token
        }
    }
    </code>
    </pre>

1. 使用步骤3中提到的令牌为客户创建一个空购物车。

   <pre>
    <code class="language-graphql">
    mutation{
     createEmptyCart
    }
    </code>
    </pre>

1. 创建一个脚本，使两个`addSimpleProductsToCart`请求并行运行。 例如：

   <pre>
    <code class="language-#!/bin/bash">
    curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MywiaWF0IjoxNjIzOTUyNjcwLCJleHAiOjE2MjM5NTYyNzB9.-fh7ysqiQTAacdB3MVvaXzFE9AmKyfF8TsVmICLJoWI" -d '{"query" : "mutation { addSimpleProductsToCart( input: { cart_id: \"S8dCF7uan1POMy0qY0Hup7tEv1AhFGdY\" cart_items: [ { data: { quantity: 2 sku: \"simple1\" } } ] } ) { cart { items { id product { name sku } quantity } } } }"}' http://magento2.3.local/graphql &
    curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MywiaWF0IjoxNjIzOTUyNjcwLCJleHAiOjE2MjM5NTYyNzB9.-fh7ysqiQTAacdB3MVvaXzFE9AmKyfF8TsVmICLJoWI" -d '{"query" : "mutation { addSimpleProductsToCart( input: { cart_id: \"S8dCF7uan1POMy0qY0Hup7tEv1AhFGdY\" cart_items: [ { data: { quantity: 1 sku: \"simple1\" } } ] } ) { cart { items { id product { name sku } quantity } } } }"}' http://magento2.3.local/graphql
    </code>
    </pre>

1. 运行脚本。

<u>预期的结果</u>：

在购物车中只创建一个总数量的产品线（在本例中为3个）。

<u>实际结果</u>：

在购物车中为同一产品创建了两个单独的行。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Adobe Commerce质量修补程序的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中可用的[修补程序部分。
