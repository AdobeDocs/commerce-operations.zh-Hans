---
title: ACSD-62755： [!DNL TinyMCE] 7需要在编辑器初始化设置中添加字体大小和字体
description: 应用ACSD-62755修补程序以修复Adobe Commerce问题，该问题导致 [!DNL TinyMCE] 7要求在编辑器初始化设置中专门添加*font size*和*font family*。
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# ACSD-62755： [!DNL TinyMCE] 7需要在编辑器初始化设置中添加字体大小和字体

ACSD-62755修补程序修复了[!DNL TinyMCE] 7要求在编辑器初始化设置中专门添加&#x200B;*字体大小*&#x200B;和&#x200B;*字体系列*&#x200B;选择器的问题。 此修补程序在安装了[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56时可用。 修补程序ID为ACSD-62755。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.5-p10

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4-p11、2.4.5-p10、2.4.6-p8、2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!DNL TinyMCE] 7要求在编辑器初始化设置中专门添加&#x200B;*字体大小*&#x200B;和&#x200B;*字体系列*&#x200B;选择器。

<u>重现步骤</u>：

转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]**，然后选择&#x200B;*[!UICONTROL Show Editor]*。

<u>预期的结果</u>：

*字体大小*&#x200B;和&#x200B;*字体系列*&#x200B;选择器在WYSIWYG编辑器中可见。

<u>实际结果</u>：

WYSIWYG编辑器中缺少&#x200B;*字体大小*&#x200B;选择器。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
