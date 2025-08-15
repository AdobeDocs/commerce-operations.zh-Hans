---
title: MDVA-44505：对购物车应用奖励点数的GraphQL查询不会更新总计
description: MDVA-44505修补程序解决了以下问题：针对应用奖励积分的购物车的GraphQL查询没有考虑奖励积分，并返回不正确的总计。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14后，即可使用此修补程序。 修补程序ID为MDVA-44505。 请注意，Adobe Commerce 2.4.3中已修复此问题。
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
exl-id: 543698d8-8963-4bf7-af82-11c2498e882e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-44505：对购物车应用奖励点数的GraphQL查询不会更新总计

MDVA-44505修补程序解决了以下问题：针对应用奖励积分的购物车的GraphQL查询没有考虑奖励积分，并返回不正确的总计。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14时，此修补程序可用。 修补程序ID为MDVA-44505。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

应用奖励积分的购物车的GraphQL查询不会考虑奖励积分，并返回不正确的总计。

<u>重现步骤</u>：

1. 配置奖励积分。
1. 创建购物车并应用一些奖励积分。
1. 从`GetCart`端点调用`GraphQL`查询并检索购物车：

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. 检查总计。
1. 现在使用Rest API (`/rest/V1/carts/mine/totals`)检查客户的购物车总计。

<u>预期的结果</u>：

购物车的GraphQL查询返回正确的总计，其中考虑了奖励积分。

<u>实际结果</u>：

GraphQL查询不考虑奖励点数并返回不正确的总计。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
