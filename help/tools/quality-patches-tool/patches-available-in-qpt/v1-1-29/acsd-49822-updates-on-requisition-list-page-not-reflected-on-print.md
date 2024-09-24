---
title: 'ACSD-49822：申请列表页面上的更新未反映在打印申请列表中'
description: 应用ACSD-49822补丁程序，以修复Adobe Commerce中申购单列表页上的更新未反映在打印申购单列表上的问题。
feature: Admin Workspace, B2B
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-49822：申请列表中的更新未反映在打印申请列表中

ACSD-49822修补程序修复了申请列表页面上的更新未反映在打印申请列表上的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-49822。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

申请列表页面上的更新未反映在打印申请列表中。

<u>重现步骤</u>：

1. 导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[B2B功能]**&#x200B;以启用申请列表。
1. 创建产品。
1. 以客户身份登录，并将两个产品添加到申请列表。
1. 转到&#x200B;**[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**。
1. 查看申请列表。
1. 单击右上角的&#x200B;**[!UICONTROL Print]**。
1. 关闭打印窗口并打印申请列表页。
1. 删除列表中的项目或更新项目的数量，然后再次尝试打印。
1. 您会发现打印窗口上的项目未更新。
1. 关闭打印窗口。
1. 您会发现申请列表打印页面上的物料未更新。

<u>预期的结果</u>：

在应用任何更改后，将更新要打印的列表。

<u>实际结果</u>：

更新未反映在申购单列表打印页面上。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
