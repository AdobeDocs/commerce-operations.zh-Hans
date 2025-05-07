---
title: ACSD-63520：通过图像上传配置上传的图像超过了配置的大小限制
description: 应用ACSD-63520补丁以修复通过“管理”面板中的图像上传配置上传的图像不符合配置的最大上传大小限制的Adobe Commerce问题。
feature: Media, Products
role: Admin, Developer
source-git-commit: 987d335f03d552763f75adb73890787abf235e66
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# ACSD-63520：通过[!UICONTROL Image Upload Configuration]上传的映像超出了配置的大小限制

ACSD-63520修补程序解决了通过[!UICONTROL Images Upload Configuration]上传的图像不符合配置的最大上传大小限制的问题。 要解决此问题，请在[!UICONTROL Admin]面板中配置[!UICONTROL Images Upload Configuration]设置。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62时，此修补程序可用。 修补程序ID为ACSD-63520。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.7

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的[!DNL Adobe Commerce]版本兼容，请将`magento/quality-patches`包更新为最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过[!UICONTROL Admin]面板中的[!UICONTROL Images Upload Configuration]上传的图像不符合最大上传大小限制。

<u>重现步骤</u>：

1. 登录到&#x200B;**[!UICONTROL Admin]**&#x200B;面板。
1. 导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]**&#x200B;并设置：
   * 质量：100
   * 启用前端调整大小：是
   * 最大宽度：800
   * 最大高度：600
1. 展开&#x200B;**[!UICONTROL Media Gallery Image Optimization]**&#x200B;并设置：
   * 启用图像优化：是
   * 最大宽度：1000
   * 最大高度：1000
1. 导航到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]**。
   1. 添加&#x200B;**[!UICONTROL Product Name]**、**[!UICONTROL SKU]**&#x200B;和&#x200B;**[!UICONTROL Price]**。
   1. 单击&#x200B;**[!UICONTROL Create Configurations]**，选择&#x200B;**[!UICONTROL Attributes]**，然后单击&#x200B;**[!UICONTROL Next]**。
   1. 选择大小(S、M、L、XL)，单击&#x200B;**[!UICONTROL Next]**。
   1. 在&#x200B;**[!UICONTROL Images]**&#x200B;下，选择&#x200B;**[!UICONTROL Apply single set of images to all SKUs]**。
   1. 上传图像（至少1024x1024），单击&#x200B;**[!UICONTROL Next]**。
   1. 单击&#x200B;**[!UICONTROL Generate Product]**。
1. 单击&#x200B;**[!UICONTROL Save]**。

<u>预期的结果</u>：

图像应遵循配置的上传大小和调整大小限制。

<u>实际结果</u>：

图像大小未调整并超出配置的上传大小限制。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
