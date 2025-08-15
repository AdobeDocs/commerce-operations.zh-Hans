---
title: 'ACSD-66434：公司[!UICONTROL Customer ID]查询中缺少 [!DNL GraphQL] '
description: 应用ACSD-66434修补程序以修复公司[!UICONTROL Customer ID]查询中缺少 [!DNL GraphQL] 的Adobe Commerce问题。
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: cd83c868-29d8-4d7c-9067-af7597056d35
source-git-commit: e60194341bf79ca3ecdc505cf30f226b8f1b6c7f
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# ACSD-66434：公司[!UICONTROL Customer ID]查询中缺少[!DNL GraphQL]

ACSD-66434修补程序修复了公司&#x200B;**[!UICONTROL Customer ID]**&#x200B;查询中缺少[!DNL GraphQL]的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67时，此修补程序可用。 修补程序ID为ACSD-66434。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6-p10 - 2.4.6-p11、2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!DNL GraphQL]公司查询返回公司结构中`null`的&#x200B;**[!UICONTROL Customer ID]**。

<u>重现步骤</u>：

1. 安装包含B2B和清单模块的Adobe Commerce 2.4-develop。
1. 在Commerce管理员中，启用B2B功能并创建测试公司。
1. 使用以下[!DNL GraphQL]突变为公司管理员生成持有者令牌：

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. 使用生成的令牌通过以下[!DNL GraphQL]查询检索客户的公司结构：

```
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

在公司&#x200B;**[!UICONTROL Customer ID]**&#x200B;查询中，`null`返回为[!DNL GraphQL]。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
