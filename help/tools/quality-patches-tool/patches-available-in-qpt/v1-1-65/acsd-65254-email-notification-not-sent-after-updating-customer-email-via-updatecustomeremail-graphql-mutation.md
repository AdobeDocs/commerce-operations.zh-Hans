---
title: ACSD-65254：通过updateCustomerEmail [!DNL GraphQL]突变更新客户电子邮件后未发送电子邮件通知
description: 应用ACSD-65254修补程序以修复Adobe Commerce问题，该问题导致在使用updateCustomerEmail [!DNL GraphQL]突变成功更新客户帐户上的电子邮件地址后，未向客户发送电子邮件通知。
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4560f5f5-d00c-5b5d-b61b-369d85ef7a26
    internal-label: User Account
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%
---
# ACSD-65254：通过`updateCustomerEmail` [!DNL GraphQL]突变更新客户电子邮件后未发送电子邮件通知

ACSD-65254修补程序修复了使用`updateCustomerEmail` [!DNL GraphQL]突变更新客户帐户上的电子邮件地址后未向客户发送电子邮件通知的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65时，此修补程序可用。 修补程序ID为ACSD-65254。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用`updateCustomerEmail` [!DNL GraphQL]突变更新客户的电子邮件地址后，未向其发送电子邮件通知。

<u>重现步骤</u>：

1. 使用以下突变创建用户：

   ```graphql
   mutation {
       createCustomer(
           input: {
               firstname: "Test"
               lastname: "User"
               email: "test@test.com"
               password: "Admin@123"
               is_subscribed: true
           }
       ) {
           customer {
               created_at
           }
       }
   }
   ```

1. 为之前创建的用户生成令牌，并将其用作持有者令牌：

   ```graphql
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
       token
   }
   }
   ```

1. 尝试使用上次创建的持有者令牌更新以前创建用户的电子邮件：

   ```graphql
   mutation {
       updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
           customer {
               email
           }
       }
   }
   ```

<u>预期的结果</u>：

客户应在更新其帐户上的电子邮件地址后收到电子邮件通知。

<u>实际结果</u>：

只向新地址发送订阅电子邮件；不发送更改电子邮件地址的确认电子邮件。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
