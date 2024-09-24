---
title: 'ACSD-56447：通过并行Web REST API将相同的产品添加到购物车中会导致购物车中有两个不同的项目'
description: 应用ACSD-56447修补程序以修复Adobe Commerce问题，该问题导致通过并行Web REST API请求将同一产品添加到购物车会在购物车中生成两个单独的项目。
feature: Shopping Cart, REST
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-56447：通过并行Web REST API将同一产品添加到购物车中会导致购物车中包含两个单独的项目

ACSD-56447修补程序修复了通过并行Web REST API请求将同一产品添加到购物车会在购物车中生成两个单独项目的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45时，此修补程序可用。 修补程序ID为ACSD-56447。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过并行Web REST API请求将同一产品添加到购物车会导致购物车中出现两个不同的项目。

<u>重现步骤</u>：

1. 生成客户令牌以使用[!DNL Postman]发出REST API调用请求。
1. 为客户创建购物车。
1. 使用上面生成的令牌为客户创建一个空购物车。
1. 使用CURL使两个`AddProductsToCart`请求并行运行。 按照开发人员文档中的[订单处理教程](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/)中的说明进行操作。

<u>预期的结果</u>：

具有多个数量的物料显示在一行中。

<u>实际结果</u>：

相同的SKU显示在多个行项目中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
