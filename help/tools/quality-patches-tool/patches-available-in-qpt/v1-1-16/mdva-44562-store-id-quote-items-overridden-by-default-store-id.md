---
title: MDVA-44562：由默认存储ID覆盖的报价单项目的存储ID
description: MDVA-44562修补程序修复了以下问题：对于GraphQL请求，默认商店ID将覆盖报价项的商店ID。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16后，即可使用此修补程序。 修补程序ID为MDVA-44562。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562：由默认存储ID覆盖的报价单项目的存储ID

MDVA-44562修补程序修复了以下问题：对于GraphQL请求，默认商店ID将覆盖报价项的商店ID。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16后，即可使用此修补程序。 修补程序ID为MDVA-44562。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

报价项目的商店ID将被GraphQL请求的默认商店ID覆盖。

<u>重现步骤</u>：

1. 创建新的商店视图。
1. 为每个商店视图创建具有不同名称的新简单产品。
1. 创建新客户。
1. 获取客户授权令牌。

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. 使用授权令牌为客户创建新报价。

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. 将产品添加到购物车。

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. 获取默认商店视图的购物车内容。

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. 获取新商店视图的购物车内容。

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>预期的结果</u>：

来自新商店视图的响应显示来自新商店视图的产品名称。

<u>实际结果</u>：

来自新商店视图的响应在默认商店视图下显示产品名称设置。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
