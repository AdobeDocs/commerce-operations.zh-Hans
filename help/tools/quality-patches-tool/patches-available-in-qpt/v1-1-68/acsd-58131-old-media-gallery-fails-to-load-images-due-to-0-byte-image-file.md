---
title: ACSD-58131：由于0字节图像文件，旧媒体集无法加载图像
description: 应用ACSD-58131修补程序以修复目录中存在长度为0字节的图像时，旧媒体库无法呈现图像的Adobe Commerce问题。
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131：由于0字节图像文件，旧媒体集无法加载图像

ACSD-58131修补程序修复了当目录中存在0字节图像时，旧媒体库无法呈现图像的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-58131。 请注意，此问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将0字节的图像放入媒体集目录后，旧媒体集无法呈现任何图像。 更新后的系统现在会跳过无效的0字节文件，按预期显示有效图像，并记录每个无效文件的警告。

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]**。
1. 将&#x200B;**[!UICONTROL Enable Old Media Gallery]**&#x200B;设置为&#x200B;*是*。
1. 在`pub/media/wysiwyg`目录中放置一些图像。
1. 使用`touch pub/media/wysiwyg/empty_image.png`在同一目录中创建0字节映像。
1. 通过页面生成器，在任何内容(例如，CMS块)下添加`wysiwyg`目录中的图像：
   1. 创建新块。 转到&#x200B;**[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]**&#x200B;并单击&#x200B;**[!UICONTROL Add New Block]**。
   1. 使用页面生成器编辑内容部分。
   1. 在&#x200B;**[!UICONTROL Layout]**&#x200B;下，将新的&#x200B;**[!UICONTROL Row]**&#x200B;拖到舞台上。
   1. 展开&#x200B;**[!UICONTROL Media]**&#x200B;并将&#x200B;**[!UICONTROL Image]**&#x200B;占位符拖入行中。
   1. 单击&#x200B;**[!UICONTROL Select from Gallery]**。
   1. 选择`wysiwyg`目录（如果默认未选择）。

<u>预期的结果</u>：

即使存在0字节的图像（或任何其他文件），介质集仍可正常工作。

<u>实际结果</u>：

由于在`wysiwyg`中记录了一个严重错误，媒体集无法从`var/log/system.log`目录加载任何图像：

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
