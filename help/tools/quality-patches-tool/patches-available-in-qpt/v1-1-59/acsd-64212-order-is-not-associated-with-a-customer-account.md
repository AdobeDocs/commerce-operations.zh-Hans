---
title: ACSD-64212：订单未链接到下订单后通过 [!DNL GraphQL] 创建的客户帐户
description: 应用ACSD-64212修补程序以修复Adobe Commerce问题，该问题导致订单无法关联到在下订单后通过 [!DNL GraphQL] 创建的客户帐户。
feature: GraphQL, Checkout, Customers
role: Admin, Developer
source-git-commit: d1d5214293f3bb38b787f80172aabf9cd0bf808b
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-64212：订单未链接到下订单后通过[!DNL GraphQL]创建的客户帐户

ACSD-64212修补程序修复了以下问题：订单未关联到在下单后通过[!DNL GraphQL]创建的客户帐户。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59时，此修补程序可用。 修补程序ID为ACSD-64212。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在发出订单后通过[!DNL GraphQL]创建帐户时，订单未链接到客户帐户。

<u>重现步骤</u>：

1. 客人可以在前台下单。
1. 发送以下请求以创建帐户：

```
mutation CreateAccountAfterCheckout(
$email: String!
$firstname: String!
$lastname: String!
$password: String!
$is_subscribed: Boolean!
) {
  createCustomer(
    input: {
      email: $email
      firstname: $firstname
      lastname: $lastname
      password: $password
      is_subscribed: $is_subscribed
    }
  ) {
    customer {
      email
      __typename
    }
    __typename
  }
}
```

```
{
  "email": "guest@example.com",
  "firstname": "first",
  "lastname": "last",
  "password": "password",
  "is_subscribed": false
}
```

<u>预期的结果</u>：

客户订单在创建客户帐户后与客户关联。

<u>实际结果</u>：

已创建客户帐户，但访客订单未与客户关联。


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
