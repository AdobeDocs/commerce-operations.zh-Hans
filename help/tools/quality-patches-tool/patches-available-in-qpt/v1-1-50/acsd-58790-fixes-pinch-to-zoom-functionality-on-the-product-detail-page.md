---
title: 'ACSD-58790：修复了 [!DNL Chrome]上移动视图中产品详细信息页面图像的缩放夹功能'
description: ACSD-58790修复了Adobe Commerce的问题，即 [!DNL Chrome] 上的移动设备视图中的图像未按预期放大图像。
feature: Storefront
role: Admin, Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-58790：修复了[!DNL Chrome]上移动视图中产品详细信息页面图像的缩放夹功能

ACSD-58790修补程序修复了Adobe Commerce问题，该问题导致[!DNL Chrome]上移动设备视图中的图像未按预期放大图像。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-58790。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了[!DNL Chrome]上移动视图中产品详细信息页面图像的缩放缩放缩放功能。

<u>重现步骤</u>：

1. 创建带图像的产品。
1. 从[!DNL Chrome]浏览器中打开产品。
1. 单击图像并验证双击是否放大图像。
1. 使用[!DNL Chrome]开发人员工具切换到移动设备视图。
1. 单击图像。
1. 双击即可。

<u>预期的结果</u>：

双击时，图像将被放大。

<u>实际结果</u>：

双击时图像未放大。 此问题特定于移动设备视图中的[!DNL Chrome]，因为缩放功能在[!DNL Firefox]中按预期工作。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
