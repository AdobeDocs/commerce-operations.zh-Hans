---
title: ACSD-61895： [!DNL GraphQL] 类别查询无法查询具有受限视图的私有共享目录
description: 应用ACSD-61895修补程序以修复Adobe Commerce问题：在为相同类别创建具有限制的私有共享目录时，来宾客户的 [!DNL GraphQL] 响应（使用具有所有允许类别的公共共享目录）未返回任何类别。
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
source-git-commit: f929f76dbe79c3764e2c157576b4f6db867673cf
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# ACSD-61895：对受限制视图的私有共享目录的[!DNL GraphQL] `categories`查询失败

ACSD-61895修补程序修复了在为同一类别创建具有限制的私有共享目录时，来宾客户的[!DNL GraphQL]响应（使用具有所有允许类别的公共共享目录）未返回任何类别的问题。

修复之后，它会返回所有具有来宾用户允许权限（公共共享目录）的类别，即使根类别在私有共享目录范围内没有允许权限。

安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-61895。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

为同一类别创建具有限制的专用共享目录时，来宾客户的[!DNL GraphQL]响应（使用具有所有允许类别的公共共享目录）不会返回任何类别。

<u>重现步骤</u>：

1. 安装Adobe Commerce和B2B以及示例数据。
1. 确保已启用B2B功能。
1. 创建两个共享目录：一个是公共目录，一个是专用目录。

   * 公共共享目录：

      * 将所有类别分配给公共目录。

   * 专用共享目录：

      * 仅将`Gear`类别及其子类别分配给专用目录。
      * 将专用目录分配给测试公司。

1. 创建公司用户：

   * 创建与链接到私有共享目录的测试公司关联的用户。
   * 确保用户登录时只能在前端访问`Gear`类别及其子类别。

1. 通过API查询类别：

   * 使用API客户端在没有客户令牌的情况下执行以下[!DNL GraphQL]查询：

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. 观察响应并验证是否返回`Gear`类别和其他类别。
1. 现在，使用客户令牌查询类别：

   * 以测试公司用户的身份登录。
   * 执行同一[!DNL GraphQL]类别查询，但包括登录用户的客户令牌。
   * 观察响应并检查是否仅返回`Gear`类别及其子类别。


<u>预期的结果</u>：

作为来宾公司用户进行查询时，应返回所有类别（按预期）。

<u>实际结果</u>：

来自`categories`查询的响应未显示任何类别。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。

