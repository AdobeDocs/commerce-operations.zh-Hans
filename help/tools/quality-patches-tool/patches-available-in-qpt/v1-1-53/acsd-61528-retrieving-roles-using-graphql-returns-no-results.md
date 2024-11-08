---
title: “ACSD-61528：使用GraphQL检索角色时未返回任何结果”
description: 应用ACSD-61528修补程序以解决Adobe Commerce问题，该问题导致使用GraphQL从公司管理员处检索角色时始终返回空结果。
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
source-git-commit: 4a02bb524fd8d1caae02d909bc9f2e3fc0112042
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528：使用GraphQL检索角色时未返回任何结果

ACSD-61258修补程序修复了以下问题：使用GraphQL从公司管理员处检索角色时，始终会返回空结果。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53时，此修补程序可用。 修补程序ID为ACSD-61528。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6-p5

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用GraphQL从公司管理员处检索角色时，角色结果始终为null。

<u>先决条件：</u>：

安装和启用Adobe Commerce B2B模块。

<u>重现步骤</u>：

1. 创建公司。
1. 以公司管理员身份登录具有以下突变的GraphQL：

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. 将生成的令牌作为`Bearer`令牌添加到&#x200B;**Authorization**&#x200B;请求标头中，并在GraphQL查询下运行：

   ```GraphQL
      {
      customer {
      email
      role{
       name
       id
      }
    }
   }
   ```

<u>预期的结果</u>：

GraphQL查询返回角色。

<u>实际结果</u>：

公司的角色为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。