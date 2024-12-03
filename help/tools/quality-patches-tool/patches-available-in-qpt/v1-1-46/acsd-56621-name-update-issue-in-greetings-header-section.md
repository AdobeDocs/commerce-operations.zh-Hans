---
title: ACSD-56621：更新后的名称未显示在公司管理员用户的问候语标头中
description: 应用ACSD-56621修补程序以修复Adobe Commerce问题，该问题导致更新的公司管理员用户的名字和姓氏未反映在问候语标头部分。
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 739c1c8c-e079-4ad7-be97-7c60b0347e12
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-56621：更新后的名称未显示在公司管理员用户的问候语标头中

ACSD-56621修补程序修复了公司管理员用户的更新后名字和姓氏未反映在问候语标头部分的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46时，此修补程序可用。 修补程序ID为ACSD-56621。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

更新的名称不会显示在公司管理员用户的问候语标题中。

<u>重现步骤</u>：

1. 导航到&#x200B;**[!UICONTROL Admin]**&#x200B;面板。
1. 转到&#x200B;**[!UICONTROL Stores]**&#x200B;并选择&#x200B;**[!UICONTROL Configuration]**。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;部分下，选择&#x200B;**[!UICONTROL B2B]**&#x200B;以启用B2B公司功能。
1. 转到&#x200B;**[!UICONTROL Storefront]**&#x200B;并注册一个新公司。
1. 以公司管理员用户身份登录。
1. 转到&#x200B;**[!UICONTROL My Account]** > **[!UICONTROL Company Users]**，并根据需要修改名字和姓氏字段。

<u>预期的结果</u>：

问候语标头部分中用户的名字和姓氏会立即更改。

<u>实际结果</u>：

仅当用户注销并再次登录时，才会更改用户的名字和姓氏。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
