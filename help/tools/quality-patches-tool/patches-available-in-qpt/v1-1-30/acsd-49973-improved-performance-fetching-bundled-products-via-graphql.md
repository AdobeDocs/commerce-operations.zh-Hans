---
title: 'ACSD-49973：改进了通过 [!DNL GraphQL]获取捆绑产品的性能'
description: 应用ACSD-49973修补程序以修复通过 [!DNL GraphQL]获取捆绑产品时发生性能下降的Adobe Commerce问题。
feature: GraphQL, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-49973：改进了通过[!DNL GraphQL]获取捆绑产品的性能

ACSD-49973修补程序改进了通过[!DNL GraphQL]获取捆绑产品的性能。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30时，此修补程序可用。 修补程序ID为ACSD-49973。 请注意，Adobe Commerce 2.4.7中已修复该问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过[!DNL GraphQL]获取捆绑产品时，性能会降低。

<u>先决条件</u>：

使用[性能工具包](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html)创建2000捆绑包产品。

<u>重现步骤</u>：

1. 启用[!DNL DB]查询记录器：

   ```
   bin/magento dev:query-log:enable
   ```

1. 执行以下[!DNL GraphQL]查询：

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. 检查`var/log/db.log`以获取`catalog_product_bundle_selection`表的请求。

<u>预期的结果</u>：

对`catalog_product_bundle_selection`表的请求不应出现在`var/log/db.log`中。

<u>实际结果</u>：

同时触发了对`catalog_product_bundle_selection`表的2000个请求，这会导致性能下降。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
