---
title: ACSD-51739：在“CompanyTeam”GraphQL请求中请求“structure_id”时出错
description: 应用ACSD-51739修补程序以修复以下Adobe Commerce问题：在“CompanyTeam”GraphQL请求中请求“structure_id”时返回错误。
exl-id: 74c78278-779d-4fb6-ba10-501b25b9f1fe
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739：在`CompanyTeam` GraphQL请求中请求`structure_id`时出错

ACSD-51739修补程序修复了在`CompanyTeam` GraphQL请求中请求`structure_id`时返回错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34时，此修补程序可用。 修补程序ID为ACSD-51739。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在`CompanyTeam` GraphQL请求中请求`structure_id`时返回错误。

<u>重现步骤</u>

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**，并将&#x200B;*[!UICONTROL Enable Company]*&#x200B;设置为&#x200B;*是*。
1. 创建公司以及公司管理员用户。
1. 创建新客户(*customer1*)，并将公司（如上面创建）分配给此客户。
1. 前端，以公司管理员用户身份登录。
1. 创建公司团队，并使用拖放操作将&#x200B;*customer1*&#x200B;分配给团队。
1. 运行以下公司GraphQl查询，其中包括带有`structure_id`的`CompanyTeam`：

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. 检查GraphQL响应。

<u>预期的结果</u>：

不会返回任何错误，并且所有请求的数据都存在于GraphQL响应中。

<u>实际结果</u>：

* 响应包含&#x200B;*内部服务器错误*。
* `var/log/exception.log`包含：

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
