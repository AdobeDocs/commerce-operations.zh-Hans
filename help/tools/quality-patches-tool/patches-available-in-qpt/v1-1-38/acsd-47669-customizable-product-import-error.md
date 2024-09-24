---
title: 'ACSD-47669：导入带有可自定义选项的产品时出现内部服务器错误'
description: 应用ACSD-47669修补程序以修复在导入带有可自定义选项的产品时出现内部服务器错误的Adobe Commerce问题。
feature: Products
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-47669：导入带有可自定义选项的产品时出现内部服务器错误

ACSD-47669修补程序修复了在使用可自定义选项导入产品期间出现内部服务器错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.38时，此修补程序可用。 修补程序ID为ACSD-47669。 请注意，Adobe Commerce 2.4.6中已修复该问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

导入带有可自定义选项的产品时出现内部服务器错误。

<u>重现步骤</u>：

1. 创建其他商店视图。 确保您有2个商店视图，例如en、UK。
1. 创建两个简单的产品，如prod1和prod2。
1. 准备一个csv文件，该文件将为每个商店视图中的产品和&#x200B;**所有商店视图**&#x200B;范围添加自定义选项。 导入此csv文件。
1. 准备另一个包含两个记录的csv文件。 第一个记录应更新专用于英国商店视图范围的“prod1”自定义选项，第二个记录应更新&#x200B;**所有商店视图**&#x200B;范围的“prod2”自定义选项。 导入第二个csv文件。

<u>预期的结果</u>：

您应该能够自定义选项，而不会出现任何错误。

<u>实际结果</u>：

出现完整性约束违规错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
