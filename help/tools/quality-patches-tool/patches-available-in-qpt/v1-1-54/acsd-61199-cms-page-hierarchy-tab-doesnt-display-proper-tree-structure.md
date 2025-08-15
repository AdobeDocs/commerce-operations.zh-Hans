---
title: ACSD-61199： CMS页面[!UICONTROL Hierarchy]选项卡未显示正确的树结构
description: 应用ACSD-61199修补程序以修复Adobe Commerce问题，该问题导致在编辑具有现有*[!UICONTROL Hierarchy]*的CMS页面时，CMS页面的*[!UICONTROL Hierarchy]*选项卡未显示正确的树结构。
feature: Page Content
role: Admin, Developer
exl-id: f541d001-9680-431a-9a62-816c2d10b6d5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199： CMS页面的[!UICONTROL Hierarchy]选项卡未显示正确的树结构

ACSD-61199修补程序修复了在使用现有&#x200B;*[!UICONTROL Hierarchy]*&#x200B;编辑CMS页面时，CMS页面的&#x200B;*[!UICONTROL Hierarchy]*&#x200B;选项卡未显示正确树结构的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54时，此修补程序可用。 修补程序ID为ACSD-61199。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在使用现有&#x200B;*[!UICONTROL Hierarchy]*&#x200B;编辑CMS页面时，CMS页面的&#x200B;*[!UICONTROL Hierarchy]*&#x200B;选项卡未显示正确的树结构。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**。
1. 创建新&#x200B;**[!UICONTROL CMS page]**。 它已被添加到位于&#x200B;*[!UICONTROL Hierarchy]*&#x200B;的网站根目录中。
1. 保存页面。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**。
1. 将任何其他现有页面添加到&#x200B;*[!UICONTROL Hierarchy]*。
1. 保存&#x200B;*[!UICONTROL Hierarchy]*。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**。
1. 编辑任何现有页面并打开&#x200B;*[!UICONTROL Hierarchy]*。

<u>预期的结果</u>：

*[!UICONTROL Hierarchy]*&#x200B;按预期加载。

<u>实际结果</u>：

*[!UICONTROL Hierarchy]*&#x200B;未加载到选项卡中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

[[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
