---
title: ACP2E-3789：通过WebAPI在产品更新时复制的媒体文件
description: 应用ACP2E-3789修补程序以修复Adobe Commerce问题，该问题导致在提供媒体ID时通过WebAPI进行产品更新会复制媒体文件。
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
exl-id: 1eaa8ed0-fde6-47c4-9339-8f5e7bce7b19
source-git-commit: f82dcd6c76ba3512e59275c26815b6bb89e53733
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACP2E-3789：通过WebAPI在产品更新时复制的媒体文件

ACP2E-3789修补程序修复了在提供媒体ID时通过WebAPI进行产品更新时复制媒体文件的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66时，此修补程序可用。 修补程序ID为ACP2E-3789。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用媒体ID通过WebAPI更新产品会导致系统复制媒体文件，而不是替换它们，使用每个API调用创建新文件，并导致图像栈积，从而过载`/pub/media/catalog/products/cache/`目录。

<u>重现步骤</u>：

1. 创建产品并添加图像。
1. 使用位于`base_url/rest/V1/products/<sku>`的REST API获取产品详细信息。
1. 执行PUT请求以更新产品，并保持`media_gallery_entrie`不变（相同的图像名称和文件）。
1. 检查更新前后的`pub/media/catalog/product/xx/yy`目录。

<u>预期的结果</u>：

当请求中包含媒体ID时，将替换图像文件。

<u>实际结果</u>：

图像复制时使用了新名称（例如，wb04-blue-1.jpg），从而导致不必要的文件栈积。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
