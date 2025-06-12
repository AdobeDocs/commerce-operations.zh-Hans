---
title: ACSD-47988：产品导出会修剪Page Builder产品描述中的HTML标记
description: 应用ACSD-47988修补程序以修复Adobe Commerce问题，该问题导致产品导出从页面生成器产品描述中裁切HTML标记。
feature: Admin Workspace, Data Import/Export, Page Builder, Products
role: Admin
exl-id: 2cb3b4ac-38df-4832-b894-b34bb3d7bbc6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-47988：产品导出会修剪Page Builder产品描述中的HTML标记

ACSD-47988修补程序修复了产品导出会从页面生成器产品描述中去除HTML标记的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26时，此修补程序可用。 修补程序ID为ACSD-47988。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品导出会修剪页面生成器产品描述中的HTML标记。

<u>重现步骤</u>：

1. 在描述中使用某个HTML创建产品。 使用页面生成器HTML元素插入HTML标记。
1. 使用Adobe Commerce的导入/导出功能导出产品。
1. 导入导出的CSV。
1. 打开产品，并检查描述下的HTML元素。

<u>预期的结果</u>：

导入相同内容后，HTML标记会保留在产品描述中。

<u>实际结果</u>：

HTML标记在导入后即会被删除。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
