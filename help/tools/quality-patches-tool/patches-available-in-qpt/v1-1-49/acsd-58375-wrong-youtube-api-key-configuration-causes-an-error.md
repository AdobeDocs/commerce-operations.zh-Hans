---
title: 'ACSD-58375：在商店视图级别添加视频时，未正确配置YouTube API密钥会导致错误'
description: 应用ACSD-58375修补程序以修复在商店视图级别添加Adobe Commerce视频时，错误的YouTube API密钥配置会导致错误的YouTube问题。
feature: Catalog Management, Configuration
role: Admin, Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-58735：在商店视图级别添加视频时，未正确配置YouTube API密钥会导致错误

ACSD-58735修补程序修复了在应用商店视图级别添加YouTube视频时，若错误的YouTube API密钥配置会导致错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49时，此修补程序可用。 修补程序ID为ACSD-58735。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

错误的YouTube API密钥配置导致在商店视图级别添加YouTube视频时出错。

<u>重现步骤</u>：

1. 转到管理员> **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**。
1. 将&#x200B;*范围*&#x200B;更改为&#x200B;*[!UICONTROL Main Website]*&#x200B;级别。
1. 添加YouTube API密钥。
1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**。
1. 选择任意产品并滚动到&#x200B;*[!UICONTROL Images and Video]*。 单击&#x200B;**[!UICONTROL Add Video]**。
1. 复制YouTube视频链接并将其粘贴到视频链接字段中。 从字段中移出。

<u>预期的结果</u>：

YouTube API密钥具有全局范围，在网站级别隐藏。

<u>实际结果</u>：

引发以下错误： *由于以下原因，视频未显示： API密钥无效。 请传递有效的API密钥*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
