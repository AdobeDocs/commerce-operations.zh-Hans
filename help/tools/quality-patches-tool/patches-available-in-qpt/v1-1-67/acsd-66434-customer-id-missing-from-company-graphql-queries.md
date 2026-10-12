---
title: ACSD-66434：公司[!DNL GraphQL]查询中缺少[!UICONTROL Customer ID]
description: 应用ACSD-66434修补程序以修复公司[!DNL GraphQL]查询中缺少[!UICONTROL Customer ID]的Adobe Commerce问题。
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: cd83c868-29d8-4d7c-9067-af7597056d35
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '324'
ht-degree: 0%
---
# ACSD-66434：公司[!DNL GraphQL]查询中缺少[!UICONTROL Customer ID]

ACSD-66434修补程序修复了公司[!DNL GraphQL]查询中缺少&#x200B;**[!UICONTROL Customer ID]**&#x200B;的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67时，此修补程序可用。 修补程序ID为ACSD-66434。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6-p10 - 2.4.6-p11、2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!DNL GraphQL]公司查询返回公司结构中&#x200B;**[!UICONTROL Customer ID]**&#x200B;的`null`。

<u>重现步骤</u>：

1. 安装包含B2B和清单模块的Adobe Commerce 2.4-develop。
1. 在Commerce管理员中，启用B2B功能并创建测试公司。
1. 使用以下[!DNL GraphQL]突变为公司管理员生成持有者令牌：

```graphql
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. 使用生成的令牌通过以下[!DNL GraphQL]查询检索客户的公司结构：

```graphql
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u>预期的结果</u>：

**[!UICONTROL Customer ID]**&#x200B;应在公司[!DNL GraphQL]查询中返回。

<u>实际结果</u>：

在公司[!DNL GraphQL]查询中，**[!UICONTROL Customer ID]**&#x200B;返回为`null`。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
