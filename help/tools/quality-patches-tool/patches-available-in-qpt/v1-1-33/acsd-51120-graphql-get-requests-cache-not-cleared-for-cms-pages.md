---
title: ACSD-51120：没有为包含GraphQL块的CMS页面清除CMS GET请求缓存
description: 应用ACSD-51120修补程序以修复包含GraphQL块的Adobe Commerce页面未清除CMS GET请求缓存的CMS问题。
exl-id: e1b84db0-2441-4729-aeeb-8486a623aebf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-51120：没有为包含GraphQL块的CMS页面清除CMS GET请求缓存

ACSD-51120修补程序修复了以下问题：对于包含通过暂存更新更新的GraphQL块的CMS页面，未清除CMS GET请求缓存。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51120。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于包含通过暂存更新更新更新的GraphQL块的CMS页面，不会清除CMS GET请求缓存。

<u>重现步骤</u>：

1. 创建CMS块。
1. 使用[!DNL Page Builder]将CMS块包含到CMS页面中。
1. 使用CMS请求获取使用给定GraphQL查询的GET页面：

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. 确保[!DNL Varnish]中缓存了GraphQL响应。
1. 为块创建计划更新。
1. 等待计划更新应用，然后运行cron作业以应用计划更新。
1. 使用CMS请求通过给定的GraphQL查询再次获取GET页面。

<u>预期的结果</u>：

响应会显示更新的内容。

<u>实际结果</u>：

响应仍显示旧内容。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
