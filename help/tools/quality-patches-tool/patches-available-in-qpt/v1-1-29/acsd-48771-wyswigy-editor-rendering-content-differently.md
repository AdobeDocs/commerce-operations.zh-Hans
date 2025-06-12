---
title: ACSD-48771：WYSIWYG编辑器以不同的方式呈现内容
description: 应用ACSD-48771修补程序以修复WYSIWYG编辑器以不同方式呈现内容的Adobe Commerce问题。
feature: Cache, Page Content
role: Admin
exl-id: 9480af54-800b-4802-b1a3-65d1a6e169ec
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-48771：WYSIWYG编辑器以不同的方式呈现内容

ACSD-48771修补程序修复了WYSIWYG编辑器以不同方式呈现内容的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-48771。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

WYSIWYG编辑器以不同的方式呈现内容。

<u>重现步骤</u>：

1. 转到Adobe Commerce管理员，创建一个新页面，其中有一行三列，然后保存该页面。
1. 请将Adobe Commerce更新至最新版本之一。
1. 将[!DNL Chrome]浏览器设置为禁用缓存和速度为&#x200B;*Fast 3G*。
1. 再次转到编辑页面并刷新该页面，直到列变为行。
1. 当列位于行中时保存页面。

<u>预期的结果</u>：

管理员页面生成器不应在行中显示列。

<u>实际结果</u>：

列显示在不同的行中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
