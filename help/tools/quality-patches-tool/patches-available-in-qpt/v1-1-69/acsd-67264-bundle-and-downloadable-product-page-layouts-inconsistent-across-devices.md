---
title: ACSD-67264：捆绑包和可下载的产品页面布局在各设备之间不一致
description: 应用ACSD-67264补丁以修复Adobe Commerce捆绑包和可下载页面由于产品信息媒体块重新排列而遇到布局问题。
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264：捆绑包和可下载的产品页面布局在各设备之间不一致

ACSD-67264修补程序修复了捆绑包和可下载产品页面布局在各设备之间不一致的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-67264。 请注意，此问题已在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于重新排列产品信息媒体块，捆绑包和可下载产品页面遇到布局问题。

<u>重现步骤</u>：

1. 安装示例数据。
1. 打开捆绑包产品页面并检查桌面上的布局。
1. 将捆绑包产品页面添加到愿望列表，导航到愿望列表，单击编辑图标，然后检查布局。
1. 对可下载的产品重复步骤2和3。

<u>预期的结果</u>：

捆绑包产品PDP在没有任何问题的情况下呈现。

<u>实际结果</u>：

捆绑产品PDP呈现为随机空间。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： Tools指南中用于优质修补程序的Self-service工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
