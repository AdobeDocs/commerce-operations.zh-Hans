---
title: 'ACSD-49129：产品媒体API响应中未返回“Content”属性'
description: 应用ACSD-49129修补程序以修复Adobe Commerce问题，该问题导致“rest/V1/products/sku/media”产品媒体API响应中未返回*content*属性（*base64图像代码*）。
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-49129：产品媒体API响应中未返回“Content”属性

ACSD-49129修补程序修复了`rest/V1/products/sku/media`产品媒体API响应中未返回&#x200B;*content*&#x200B;属性(*[!UICONTROL base64 image code]*)的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.30时，此修补程序可用。 修补程序ID为ACSD-49129。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`rest/V1/products/sku/media`产品媒体API响应中未返回&#x200B;*content*&#x200B;属性(*[!UICONTROL base64 image code]*)。

<u>重现步骤</u>：

1. 创建带图像的产品。
1. 将&#x200B;*GETREST API*&#x200B;请求发送到`rest/V1/products/<sku>/media`和`rest/V1/products/<sku>/media/<entryId>`。
1. 检查API响应。

<u>预期的结果</u>

包含数据的&#x200B;*content*&#x200B;属性可通过REST API使用。

<u>实际结果</u>

API响应中不存在&#x200B;*content*&#x200B;属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
