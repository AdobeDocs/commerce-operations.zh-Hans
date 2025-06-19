---
title: ACSD-63793：导入进程在不同浏览器选项卡中相互干扰
description: 应用ACSD-63793修补程序以修复导入过程在不同浏览器选项卡中相互干扰的Adobe Commerce问题。
feature: Data Import/Export
role: Admin, Developer
exl-id: f6bed4c4-5ea2-47e7-97fa-d7717470297f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-63793：导入进程在不同浏览器选项卡中相互干扰

ACSD-63793修补程序修复了导入过程在不同浏览器选项卡中相互干扰的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59时，此修补程序可用。 修补程序ID为ACSD-63793。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过管理员UI导入数据会干扰其他导入，导致来自一个导入的数据在另一个导入中进行处理。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**。
1. 将&#x200B;**[!UICONTROL Entity Type]**&#x200B;设置为&#x200B;*[!UICONTROL Customers and Addresses]（单个文件）*。
1. 将&#x200B;**[!UICONTROL Import Behavior]**&#x200B;设置为&#x200B;*[!UICONTROL Add/Update]*。
1. 选择要导入的有效文件。
1. 单击&#x200B;**[!UICONTROL Check Data]**&#x200B;按钮。
1. 保持此选项卡打开。
1. 打开新选项卡，并使用包含无效数据的文件重复这些步骤（例如，针对不同客户的两封相同的电子邮件）。
1. 切换回第一个选项卡。
1. 单击底部的&#x200B;**[!UICONTROL Import]**&#x200B;按钮。

<u>预期的结果</u>：

导入过程不应相互干扰。

<u>实际结果</u>：

导入过程完成，报表文件可供下载。 它指示第二行中有错误，并且会处理来自其他导入的数据，即使初始验证传递时没有任何错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
