---
title: ACSD-65775：多个数量的REST API订单详细信息中的“base_row_total”和“row_total”值不正确
description: 应用ACSD-65775修补程序以修复Adobe Commerce问题，该问题导致在订购同一物料的多个数量时，REST API订单详细信息返回错误的“base_row_total”和“row_total”值。
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 23c78abaf28f64baf0e91bcaf89bd0e34b5bf78a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# ACSD-65775：多个数量的REST API订单详细信息中的`base_row_total`和`row_total`值不正确

ACSD-65775修补程序修复了在订购同一项目的多个数量时，REST API订单详细信息返回错误的`base_row_total`和`row_total`值的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66时，此修补程序可用。 修补程序ID为ACSD-65775。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订购同一物料的多个数量时，订单详细信息REST API响应中的`base_row_total`和`row_total`显示单价而不是总价。

<u>重现步骤</u>：

1. 创建两个简单的产品：simple1定价为10美元，simple2定价为15美元。
1. 创建新的客户帐户。
1. 将simple1添加到数量为2的购物车，并将simple2添加到数量为3的购物车。
1. 使用客户帐户下订单。
1. 通过向`/rest/V1/integration/admin/token`发送具有以下有效负载的POST请求获取管理令牌：

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. 使用GET请求向`/rest/default/V1/orders/1`检索订单详细信息。

<u>预期的结果</u>：

`base_row_total`和`row_total`应反映总价，计算方式为数量乘以项目价格(例如，2 × $10 = $20 for simple1)。

<u>实际结果</u>：

`base_row_total`和`row_total`仅返回单价（例如，simple1为$10，而不是$20）。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
