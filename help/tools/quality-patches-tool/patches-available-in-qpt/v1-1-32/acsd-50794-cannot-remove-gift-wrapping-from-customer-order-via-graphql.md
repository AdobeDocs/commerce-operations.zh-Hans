---
title: ACSD-50794：无法通过GraphQL从客户订单中删除礼品包装
description: 应用ACSD-50794修补程序以修复Adobe Commerce问题，该问题导致用户无法通过GraphQL从客户订单中删除礼品包装。
feature: Gift, GraphQL, Orders
role: Admin
exl-id: e088fb18-89d3-47e4-ad02-54068c1ab653
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-50794：无法通过GraphQL从客户订单中删除礼品包装

ACSD-50794修补程序修复了用户无法通过GraphQL从客户订单中删除礼品包装的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32时，此修补程序可用。 修补程序ID为ACSD-50794。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户无法通过GraphQL从客户订单中删除礼品包装。

<u>重现步骤</u>：

1. 从前端创建客户。
1. 创建一个简单的产品。
1. 通过转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]**&#x200B;并设置&#x200B;*[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*&#x200B;来启用&#x200B;*[!UICONTROL Gift Messages]*。
1. 通过转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**&#x200B;创建&#x200B;*[!UICONTROL Gift Wrapping]*。
1. 获取客户令牌。
1. 创建一个空购物车customerCart。
   * 将产品添加到购物车： `addProductsToCart`突变
   * 设置帐单地址： `setBillingAddressOnCart`突变
   * 设置配送地址： `setShippingAddressesOnCart`突变
   * 设置配送方式： `setShippingMethodsOnCart`变异（扁平化）
   * 设置付款方式： `setPaymentMethodOnCart`突变(checkmo)
1. 现在使用此购物车查询检查礼品包装&#x200B;*Uid*：

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. 使用`setGiftOptionsOnCart`设置礼品包装。
1. 检查购物车：购物车查询。
1. 使用`setGiftOptionsOnCart`取消设置礼品包装（将值设置为null）。
1. 再次检查购物车：购物车查询。
1. 排序： `placeOrder`突变。
1. 运行客户查询：客户。

   ```GraphQL
   query {
     customer {
       firstname
       middlename
       lastname
       suffix
       email
       orders {
           items {
               order_date
               gift_wrapping {
                   design
                   uid
               }
           }
       }
       addresses {
         firstname
         middlename
         lastname
         street
         city
         region {
           region_code
           region
         }
         postcode
         country_code
         telephone
       }
     }
   }
   ```

<u>预期的结果</u>：

一旦用户设置了礼品包装并取消设置，客户查询将返回空值。

<u>实际结果</u>：

客户查询仍会按应用情况返回礼品包装。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
