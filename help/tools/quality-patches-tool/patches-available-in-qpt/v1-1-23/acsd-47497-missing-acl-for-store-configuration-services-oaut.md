---
title: 'ACSD-47497：存储/配置/服务[!UICONTROL OAuth]缺少ACL'
description: 当为特定角色设置了权限，并且您无法定义对配置部分的访问权限时，应用ACSD-47497修补程序以修复Adobe Commerce问题。
feature: Configuration, Identity Management, Services
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-47497：存储/配置/服务[!UICONTROL OAuth]缺少ACL

ACSD-47497修补程序解决了&#x200B;**[!UICONTROL Services]**&#x200B;选项卡在Adobe Commerce管理员的&#x200B;**[!UICONTROL Configuration]**&#x200B;部分中不可见的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23时，此修补程序可用。 修补程序ID为ACSD-47497。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

为特定角色设置权限后，您无法定义对&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**&#x200B;的访问权限。

<u>重现步骤</u>：

1. 登录到Adobe Commerce管理员。 转到&#x200B;**[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**。
1. 在Administrators角色中选择&#x200B;**[!UICONTROL Role Resources]**，并将&#x200B;**[!UICONTROL Roles Resources]**&#x200B;下的&#x200B;**[!UICONTROL Resource Access]**&#x200B;设置为&#x200B;_自定义_，然后选中所有复选框。 选择&#x200B;**[!UICONTROL Save Role]**。
1. 选择&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]**。 **[!UICONTROL OAuth]**&#x200B;配置部分不可用。

<u>预期的结果</u>：

在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**&#x200B;中，配置部分可见。

<u>实际结果</u>：

在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**&#x200B;中，缺少配置部分。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
