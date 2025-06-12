---
title: ACSD-54067：产品视频不会在移动设备上播放
description: 应用ACSD-54067修补程序以修复在移动设备上无法播放产品视频的Adobe Commerce问题。
feature: Media, Products
role: Admin, Developer
exl-id: 023e7cf7-c344-4e86-850d-741b85df87a9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54067：产品视频不会在移动设备上播放

ACSD-54067修补程序修复了产品视频无法在移动设备上播放的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41时，此修补程序可用。 修补程序ID为ACSD-54067。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品视频无法在移动设备上播放。

<u>重现步骤</u>：

1. 安装Adobe Commerce。
1. 运行以下命令：
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`。
1. 转到&#x200B;**[!UICONTROL Admin product list]**&#x200B;页并按&#x200B;*[!UICONTROL SKU product_dynamic_120]*&#x200B;筛选。
1. 打开产品页面，然后转到&#x200B;**[!UICONTROL Images and Videos]** >添加视频>填写URL： https://vimeo.com/347119375并保存。
1. 转到店面并打开&#x200B;*[!UICONTROL product_dynamic_120]*&#x200B;的产品页面。
1. 将浏览器设置为宽度为&#x200B;*320px*&#x200B;的&#x200B;*移动设备*&#x200B;并刷新。
1. 在图库滑块中，选择视频并单击以播放。

<u>预期的结果</u>：

播放产品视频。

<u>实际结果</u>：

产品视频无法播放。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
