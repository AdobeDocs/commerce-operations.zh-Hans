---
title: ACSD-58325：即使在发生验证错误后，[!UICONTROL Import]按钮也可用
description: 应用ACSD-58325修补程序以修复Adobe Commerce问题，该问题导致[!UICONTROL Import]按钮在验证错误后仍可用。
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# ACSD-58325：即使在发生验证错误后，[!UICONTROL Import]按钮也可用

ACSD-58325修补程序修复了&#x200B;**[!UICONTROL Import]**&#x200B;按钮在验证错误后仍可用的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-58325。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使在发生验证错误后，[!UICONTROL Import]按钮也可用。

<u>重现步骤</u>：

1. 为产品导入创建CSV文件，并在文件中使用不正确的图像名称。
1. 使用创建的CSV文件创建计划产品导入。
1. 等待执行计划的导入。
1. 检查[!UICONTROL Last outcome]网格中的&#x200B;**[!UICONTROL Scheduled Imports/Exports]**。

<u>预期的结果</u>：

[!UICONTROL Last outcome]应为[!UICONTROL Failed]。

<u>实际结果</u>：

[!UICONTROL Last outcome]是[!UICONTROL Successful]。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
