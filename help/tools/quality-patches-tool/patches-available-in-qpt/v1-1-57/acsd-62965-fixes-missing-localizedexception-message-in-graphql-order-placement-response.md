---
title: ACSD-62965：修复了GraphQL订单放置响应中缺少LocalizedException消息的问题
description: Adobe Commerce应用ACSD-62965修补程序以修复以下问题：在下达订单期间，GraphQL响应中未包含“LocalizedException”消息。
feature: Orders, GraphQL
role: Admin, Developer
exl-id: cf9d1409-6fe3-4019-9207-df5f12a41505
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-62965：修复了GraphQL订单放置响应中缺少`LocalizedException`消息的问题

ACSD-62965修补程序修复了在下单过程中GraphQL响应中未包含`LocalizedException`消息的问题。 此修补程序在[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57中可用。修补程序ID为ACSD-62965。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL订单响应不包含`LocalizedException`消息，导致调试的错误详细信息不足。

<u>重现步骤</u>：

1. 安装干净的&#x200B;**[!DNL Adobe Commerce]**&#x200B;实例。
1. 将产品添加到购物车并继续执行订单下达步骤。
1. 在`app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php`中将`LocalizedException`添加到`Magento\Framework\Exception\LocalizedException`。
1. 在以下行后插入例外：

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   添加例外：

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. 执行下单GraphQL请求：

   ```
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. 观察响应：
   1. 响应不包含`LocalizedException`消息。
   1. 错误响应的示例：

      ```
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u>预期的结果</u>：

如果发生`LocalizedException`，则应将异常消息包含在订单放置GraphQL响应中，以改进错误处理。

<u>实际结果</u>：

如果发生`LocalizedException`，则订单安排GraphQL响应中不包含异常消息。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
