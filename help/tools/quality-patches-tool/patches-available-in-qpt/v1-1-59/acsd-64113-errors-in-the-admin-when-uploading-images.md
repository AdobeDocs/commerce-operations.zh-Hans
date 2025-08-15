---
title: ACSD-64113：通过 [!DNL Media Gallery]上载宽度小于高度的图像时，管理员出错
description: Adobe Commerce应用ACSD-64113修补程序以修复以下问题：通过 [!DNL Media Gallery]上传宽度与其高度相比相对较小（反之亦然）的图像时，管理员中出现错误。
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64113：通过[!DNL Media Gallery]上载宽度小于高度的图像时管理员出错

ACSD-64113修补程序修复了在通过[!DNL Media Gallery]上载宽度与其高度相比相对较小（反之亦然）的图像时，管理员中发生错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59时，此修补程序可用。 修补程序ID为ACSD-64113。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过[!DNL Media Gallery]上载宽度与其高度相比相对较小的图像（反之亦然）时，管理员中会发生错误。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]**&#x200B;并选择&#x200B;**[!UICONTROL wysiwyg]**&#x200B;目录。
1. 上载宽度与其高度相比相对较小的图像（反之亦然）。

<u>预期的结果</u>：

上传图像时没有出现错误。

<u>实际结果</u>：

1. 引发以下错误消息：

   *服务器出现技术问题并生成错误。 重试以继续您正在执行的操作。 如果问题仍然存在，请稍后再试。*
1. `var/log/exception.log`包含：

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   或

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
