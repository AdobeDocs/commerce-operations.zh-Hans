---
title: ACSD-49973：改进了通过[!DNL GraphQL]获取捆绑产品的性能
description: 应用ACSD-49973修补程序以修复通过[!DNL GraphQL]获取捆绑产品时发生性能下降的Adobe Commerce问题。
feature: GraphQL, Products
role: Admin
exl-id: d4817522-65dd-4ac8-8759-8518818684ed
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%
---
# ACSD-49973：改进了通过[!DNL GraphQL]获取捆绑产品的性能

ACSD-49973修补程序改进了通过[!DNL GraphQL]获取捆绑产品的性能。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30时，此修补程序可用。 修补程序ID为ACSD-49973。 请注意，Adobe Commerce 2.4.7中已修复该问题。

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

   ```shell
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

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)

## 相关阅读

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题
* [在Commerce实施行动手册中修改数据库表的最佳实践](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications)

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
