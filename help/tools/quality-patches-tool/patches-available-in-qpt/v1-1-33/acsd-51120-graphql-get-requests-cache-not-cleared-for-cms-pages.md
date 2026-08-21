---
title: ACSD-51120：对于包含GraphQL块的CMS页面，未清除CMS GET请求缓存
description: 应用ACSD-51120修补程序以修复以下问题：对于包含GraphQL块的CMS页面，未清除CMS GET请求缓存。
exl-id: e1b84db0-2441-4729-aeeb-8486a623aebf
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-51120：对于包含GraphQL块的CMS页面，未清除CMS GET请求缓存

ACSD-51120修补程序修复了以下问题：对于包含通过暂存更新更新的GraphQL块的CMS页面，未清除CMS GET请求缓存。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51120。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于包含通过暂存更新更新更新的GraphQL块的CMS页面，不会清除CMS GET请求缓存。

<u>重现步骤</u>：

1. 创建CMS块。
1. 使用[!DNL Page Builder]将CMS块包含到CMS页面中。
1. 使用GET请求获取使用给定GraphQL查询的“CMS”页面：

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
1. 通过GET请求，使用给定的GraphQL查询再次获取CMS页面。

<u>预期的结果</u>：

响应会显示更新的内容。

<u>实际结果</u>：

响应仍显示旧内容。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
