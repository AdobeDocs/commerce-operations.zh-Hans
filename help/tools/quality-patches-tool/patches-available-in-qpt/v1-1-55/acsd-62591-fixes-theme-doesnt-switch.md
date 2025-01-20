---
title: ACSD-62591：配置**[!UICONTROL User Agent Rules]**时主题不会切换
description: 应用ACSD-62591修补程序以修复在配置**[!UICONTROL User Agent Rules]**时主题无法正确切换的Adobe Commerce问题。
feature: Themes
role: Admin, Developer
exl-id: 7b206b25-8918-40a6-a956-d38d5058d38f
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# ACSD-62591：配置[!UICONTROL User Agent Rules]时主题未正确切换

ACSD-62591修补程序修复了在配置&#x200B;**[!UICONTROL User Agent Rules]**&#x200B;时主题无法正确切换的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-62591。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

配置&#x200B;**[!UICONTROL User Agent Rules]**&#x200B;时，主题无法正确切换。

<u>重现步骤</u>：

1. 打开Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**。
1. 编辑商店视图主题。
1. 在&#x200B;**[!UICONTROL User Agent Rules]**&#x200B;中设置`/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i`并选择其他主题。
1. 保存更改并清除缓存。
1. 在移动设备上打开店面页面。
1. 从桌面浏览器中打开同一页面。

<u>预期的结果</u>：

桌面浏览器和移动设备使用其各自的主题来显示页面。

<u>实际结果</u>：

桌面浏览器显示带有移动主题的缓存页面。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。

