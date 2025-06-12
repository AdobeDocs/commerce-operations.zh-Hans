---
title: '[!DNL ACSD-47280]：禁用共享目录会提供错误的产品搜索结果'
description: 应用 [!DNL ACSD-47280] 修补程序可修复在禁用共享目录功能时显示正确搜索结果的错误。
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# [!DNL ACSD-47280]：禁用共享目录会给出错误的产品搜索结果

在禁用[!DNL shared catalog]功能时，[!DNL ACSD-47280]修补程序修复了正确搜索结果的显示。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.22时，此修补程序可用。 [!DNL patch ID]是[!DNL ACSD-47280]。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用[!DNL patch ID]作为搜索关键字来查找修补程序。

## 问题

禁用[!DNL shared catalog]会给出错误的产品搜索结果。

<u>先决条件</u>：

* 已安装[!DNL B2B]个模块

<u>重现步骤</u>：

1. 创建第二个网站。
1. 将产品分配给第二个网站。
1. 使用[!DNL GraphQL]检查&#x200B;**秒网站**&#x200B;上的产品：

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. 在默认[!DNL scope]上启用&#x200B;**[!UICONTROL Shared Catalog]**。
1. [!DNL GraphQL]请求不再显示第二个网站的任何产品，这是正确结果。
1. 转到第二个网站的[!DNL scope]并禁用&#x200B;**[!UICONTROL Company]**。

<u>预期的结果</u>：

[!DNL GraphQL]请求仍应显示第二个网站的产品。

<u>实际结果</u>：

[!DNL GraphQL]请求未显示第二个网站的任何产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
