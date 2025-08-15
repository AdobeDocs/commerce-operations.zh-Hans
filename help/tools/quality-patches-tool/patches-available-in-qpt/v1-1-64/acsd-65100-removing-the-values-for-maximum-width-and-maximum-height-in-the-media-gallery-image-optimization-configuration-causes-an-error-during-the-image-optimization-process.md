---
title: ACSD-65100：删除[!UICONTROL Maximum Width]配置中的[!UICONTROL Maximum Height]和[!UICONTROL Media Gallery Image Optimization]值会导致错误
description: 应用ACSD-65100修补程序以修复Adobe Commerce问题，该问题导致在图像优化过程中删除[!UICONTROL Maximum Width]配置中的[!UICONTROL Maximum Height]和[!UICONTROL Media Gallery Image Optimization]值会导致错误。
feature: Media
role: Admin, Developer
exl-id: 86197602-19a1-41c2-b129-1f695f303ce5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-65100：删除[!UICONTROL Maximum Width]配置中的[!UICONTROL Maximum Height]和[!UICONTROL Media Gallery Image Optimization]值会导致错误

ACSD-65100修补程序修复了在映像优化过程中删除&#x200B;**[!UICONTROL Maximum Width]**&#x200B;配置中的&#x200B;**[!UICONTROL Maximum Height]**&#x200B;和&#x200B;**[!UICONTROL Media Gallery Image Optimization]**&#x200B;值会导致错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64时，此修补程序可用。 修补程序ID为ACSD-65100。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在图像优化过程中，当&#x200B;**[!UICONTROL Maximum Width]**&#x200B;配置中移除&#x200B;**[!UICONTROL Maximum Height]**&#x200B;和&#x200B;**[!UICONTROL Media Gallery Image Optimization]**&#x200B;的值时出现错误。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]**。
1. 删除&#x200B;**[!UICONTROL Maximum Width]**&#x200B;和&#x200B;**[!UICONTROL Maximum Height]**&#x200B;的值。
1. 清除配置缓存。
1. 导航到&#x200B;**[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**。
1. 打开任意页面进行编辑。
1. 在内容区域中：
   1. 选择&#x200B;**[!UICONTROL Add Layout]** > **[!UICONTROL Row]**。
   1. 选择&#x200B;**[!UICONTROL Add Elements]** > **[!UICONTROL Text]**。
   1. 在WYSIWYG编辑器中，单击&#x200B;**[!UICONTROL Add Image]**。
   1. 上传图像并选择&#x200B;**[!UICONTROL Add Selected]**。
1. 检查`var/log/exception.log`文件。

<u>预期的结果</u>：

没有错误。

<u>实际结果</u>：

将记录与以下内容类似的错误：

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
