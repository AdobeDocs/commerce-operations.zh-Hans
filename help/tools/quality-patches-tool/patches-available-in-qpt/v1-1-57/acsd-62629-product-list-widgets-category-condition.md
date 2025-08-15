---
title: ACSD-62629：小组件中的产品列表显示不正确的类别
description: 应用ACSD-62629修补程序以修复构件中使用的产品列表不符合类别条件的Adobe Commerce问题。
feature: Page Content
role: Admin, Developer
exl-id: a7d6bd43-4b8b-48c4-ae9a-4093ac3a4110
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-62629：小组件中的产品列表显示不正确的类别

ACSD-62629修补程序修复了小组件中使用的产品列表不符合类别条件的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-62629。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

构件中使用的产品列表不遵循类别条件。

<u>重现步骤</u>：

1. 创建一个名为TEST的[!UICONTROL simple product]并将其添加到类别1。
1. 创建没有TEST产品结束日期的暂存更新。 等待更新变为活动状态。
1. 创建一个名为TEST 2的[!UICONTROL configurable product]（包含两个子产品），并将其添加到类别2。
1. 创建另一个名为TEST 5的[!UICONTROL simple product]并将其添加到类别1。
1. 运行完全重新索引。
1. 导航到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**&#x200B;并编辑主页。
1. 添加一个[!UICONTROL Products]构件，其中&#x200B;*[!UICONTROL Appearance]*&#x200B;设置为&#x200B;*[!UICONTROL Product Carousel]*，*[!UICONTROL Category]*&#x200B;设置为“类别2”。 保存页面。
1. 转到前端并打开主页。

<u>预期的结果</u>：

页面上应仅显示TEST 2（可配置）产品。

<u>实际结果</u>：

页面上同时存在TEST 5（简单）和TEST 2（可配置）产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
