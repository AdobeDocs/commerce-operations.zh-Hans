---
title: ACSD-53204： *无法保存产品*向图库添加图像的并发请求出错
description: 应用ACSD-53204修补程序以修复以下Adobe Commerce问题：*无法保存产品*在使用rest/V1/products/&amp；lt；sku&amp；gt；/media端点向产品库添加图像的并发请求时会引发错误。
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: 7fdf41e5-46ef-4505-b8ce-c330bd899fa1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53204：向图库添加图像的并发请求中出现“*无法保存产品*”错误

ACSD-53204修补程序修复了在使用`rest/V1/products/<sku>/media`端点向产品库添加图像的并发请求中抛出“*无法保存产品*”错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.39时，此修补程序可用。 修补程序ID为ACSD-53204。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用`rest/V1/products/<sku>/media`端点向产品库添加图像的并发请求时引发了“*无法保存产品*”错误。

<u>重现步骤</u>：

1. 登录到“管理面板”。
1. 使用SKU p1创建产品。
1. 向`rest/V1/products/<sku>/media`端点发出多个并发请求以同时上传多个图像。

<u>预期的结果</u>：

保存图像时不会出错。

<u>实际结果</u>：

“*无法保存产品*”错误不时返回。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
