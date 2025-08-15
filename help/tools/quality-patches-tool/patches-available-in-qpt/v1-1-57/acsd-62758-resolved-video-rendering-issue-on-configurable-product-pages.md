---
title: ACSD-62758：解决了可配置产品页面上的视频渲染问题
description: 应用ACSD-62758修补程序以修复当URL包含预先选定的样本选项时，可配置产品详细信息页面上的产品视频无法正确呈现的Adobe Commerce问题。
feature: Catalog Management
role: Admin, Developer
exl-id: 084b497d-4471-4458-bc1d-2a452bfe2662
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-62758：解决了可配置产品页面上的视频渲染问题

ACSD-62758修补程序修复了当URL包含预先选定的样本选项时，可配置产品详细信息页面上的产品视频无法正确呈现的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-62758。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当URL包含预选择的样本选项时，产品视频无法在可配置产品详细信息页面上正确呈现，从而导致显示静态图像而不是视频。

<u>重现步骤</u>：

1. 导航到[!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product]。
1. 选择&#x200B;**[!UICONTROL Color]**&#x200B;属性并编辑它。
1. 更新以下设置：
   1. 将[!UICONTROL Catalog Input Type for Store Owner]设置为[!UICONTROL Visual Swatch]。
   1. 将&#x200B;**[!UICONTROL Update Product Preview Image]**&#x200B;设置为&#x200B;**[!UICONTROL Yes]**。
1. 为此属性创建几个选项。
1. 使用&#x200B;**[!UICONTROL Color]**&#x200B;属性创建新类别并向其添加新可配置产品。
1. 将单个随机图像添加到父产品。
1. 编辑新创建的可配置子产品并将视频添加到其媒体集中：
   1. 单击&#x200B;**[!UICONTROL Add Video]**&#x200B;并使用测试视频URL： https://vimeo.com/12860646。
1. 保存产品、清除缓存并重新索引存储。
1. 在店面中打开新创建的产品，选择其中一个色板选项，并确认视频在显示播放器按钮的情况下正确加载。
1. 视频应按预期加载，并且应会显示播放器按钮。
1. 现在，右键单击其中一个样本选项，选择&#x200B;**[!UICONTROL Inspect]**，然后找到属性ID和选项ID。 复制产品URL并在其末尾附加以下内容： `www.product-url.com/producit-test#attribute_id=option_id`。 这将预先选择样本选项。 在新窗口中打开更新的URL。

<u>预期的结果</u>：

视频应正确加载，与手动选择样本选项时类似。

<u>实际结果</u>：

将显示静态图像而不是视频。 将记录控制台错误，指示视频初始化失败。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。

