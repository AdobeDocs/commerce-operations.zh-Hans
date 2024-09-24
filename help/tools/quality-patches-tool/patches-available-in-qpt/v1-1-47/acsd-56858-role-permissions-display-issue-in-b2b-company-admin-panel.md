---
title: 'ACSD-56858：B2B公司管理员中的角色权限差异'
description: 应用ACSD-56858修补程序以修复Adobe Commerce问题，该问题导致在B2B环境中，角色权限无法正确显示给受限制的公司管理员。
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-56858：B2B公司管理员中的角色权限差异

ACSD-56858修补程序修复了以下问题：在B2B环境中，针对受限制的公司管理员的角色权限显示不正确。 安装[!DNL Quality Patches Tool (QPT)] 1.1.47时，此修补程序可用。 修补程序ID为ACSD-56858。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

B2B环境中受限制公司管理员的角色权限显示不准确。

<u>重现步骤</u>：

1. 首先，设置公司，添加公司管理员和公司用户。
1. 以公司管理员身份登录店面，并为不同用户创建各种角色。
1. 根据需要分配这些角色，例如限制某些任务的访问权限，同时允许其他任务的完全访问权限。
1. 将这些角色以完全访问权限分配给公司管理员以外的用户。
1. 登录到非公司管理员用户，例如company_manager。
1. 导航到&#x200B;**[!UICONTROL Roles and permission]**&#x200B;并编辑角色。
1. 请注意，显示的权限与公司数据库中为该角色ID设置的权限不匹配。

<u>预期的结果</u>：

对于非公司管理员用户，角色和权限正确显示。

<u>实际结果</u>：

根据权限表中的数据库记录，非公司管理员用户的角色显示不正确。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
