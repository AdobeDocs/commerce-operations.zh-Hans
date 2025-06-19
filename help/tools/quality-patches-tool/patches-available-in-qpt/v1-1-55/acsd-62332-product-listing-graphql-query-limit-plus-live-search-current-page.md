---
title: ACSD-62332：产品列表GraphQL查询限制为10,000个产品， [!DNL Live Search] 将当前页设置为1
description: 应用ACSD-62332修补程序以修复Adobe Commerce问题，该问题导致产品列表GraphQL查询被限制为total_count为10,000个产品，并且，当通过GraphQL进行查询时， [!DNL Live Search] 将搜索条件中的当前页面设置为*1*而不是页面*2*。
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 3623a337-32e9-468b-a82b-6a7f7fa943c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332：产品列表GraphQL查询限制为10,000个产品，[!DNL Live Search]将当前页设置为1

>[!NOTE]
>
>此修补程序是[ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md)的更新版本，在2.4.6 - 2.4.6-p8版本上取代了[ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md)。 有关详细信息，请参阅相应的文章。

ACSD-62332修补程序修复了以下问题：产品列表GraphQL查询被限制为10,000个产品中的`total_count`，以及当通过GraphQL进行查询时，[!DNL Live Search]将搜索条件中的当前页面设置为&#x200B;*1*&#x200B;而不是页面&#x200B;*2*。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-62332。 请注意，Adobe Commerce 2.4.7中已修复这些问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品列表GraphQL查询限制为total_count为10,000个产品，其中[!DNL Live Search]在通过GraphQL查询时将搜索条件中的当前页面设置为&#x200B;*1*&#x200B;而不是&#x200B;*2*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
