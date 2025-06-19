---
title: ACSD-49877：视频自动播放在移动设备 [!DNL Safari]上不起作用
description: Adobe Commerce应用ACSD-49877修补程序以修复以下问题：当视频直接链接到远程视频文件时，视频自动播放选项在移动设备 [!DNL Safari] 上不起作用。
feature: CMS
role: Admin
exl-id: aa2557e2-4bed-4004-b9bc-36c59f1e9cdc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-49877：视频自动播放在移动设备[!DNL Safari]上不起作用

ACSD-49877修复了当视频直接链接到远程视频文件时，移动设备[!DNL Safari]上的自动播放选项不起作用的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30时，此修补程序可用。 修补程序ID为ACSD-49877。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将[！magento/quality-patches]程序包更新为最新版本，并检查[[!DNL Quality Patches Tool]：搜索修补程序]上的兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当视频直接链接到远程视频文件而不是流服务时，视频自动播放在移动设备[!DNL Safari]上不起作用。

<u>先决条件</u>：
已安装[!DNL Page Builder]个模块。

<u>重现步骤</u>：

1. 创建新的CMS页面，并使用[!DNL Page Builder]编辑&#x200B;**[!UICONTROL Content Value]**。
1. 向内容添加&#x200B;*Tab*&#x200B;元素，并在&#x200B;*Tab*&#x200B;内添加&#x200B;*视频元素*。
1. 现在，单击齿轮按钮以编辑&#x200B;*视频元素*。
1. 将指向mp4视频文件的链接添加到[!UICONTROL Video URL]字段。
1. 将&#x200B;**[!UICONTROL Autoplay]**&#x200B;字段标记为&#x200B;*是*。
1. 单击&#x200B;**[!UICONTROL Save]**。
1. 使用iPhone在[!DNL Safari]上打开最近创建的页面。

<u>预期的结果</u>

自动播放选项在使用iPhone的[!DNL Safari]上工作。

<u>实际结果</u>

使用iPhone的[!DNL Safari]上无法自动播放选项。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
