---
title: ACSD-49527：GraphQL公司角色未正确显示分页
description: 应用ACSD-49527修补程序以修复GraphQL公司角色无法正确显示分页的Adobe Commerce问题。
feature: B2B, GraphQL, Companies, Roles/Permissions
role: Admin
exl-id: 2fbc80ad-5a15-471b-99f0-213609ab3978
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-49527：GraphQL公司角色未正确显示分页

ACSD-49527修补程序修复了GraphQL公司角色无法正确显示分页的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-49527。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL公司角色未正确显示分页。

<u>重现步骤</u>：

1. 启用B2B公司。
1. 在店面，创建一个新公司。
1. 为此公司至少创建两个新角色，因此总共有三个角色，因为默认具有一个角色。
1. 发送GraphQL请求以获取指定[!UICONTROL pageSize]的角色： 2.

   ```GraphQL
   query {
       company {
           roles(pageSize: 2, currentPage: 1) {
               items {
                   name
               }
               total_count
               page_info {
                   total_pages
                   current_page
               }
           }
       }
   } 
   ```

1. 检查GraphQL响应。

<u>预期的结果</u>：

GraphQL响应中返回`total_count: 3`和`total_pages: 2`。

<u>实际结果</u>：

GraphQL响应中返回`total_count: 2`和`total_pages: 1`。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
