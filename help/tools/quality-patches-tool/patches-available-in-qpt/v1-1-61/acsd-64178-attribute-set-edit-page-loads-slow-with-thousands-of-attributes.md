---
title: ACSD-64178： [!UICONTROL Edit Attribute Set]页面加载缓慢，具有数千个产品属性
description: 应用ACSD-64178修补程序以修复Adobe Commerce问题：如果存在数千个产品属性，则[!UICONTROL Edit Attribute Set]页面加载缓慢。
feature: Catalog Management
role: Admin, Developer
exl-id: 959d825d-1b7b-49f0-b49f-64e149106e91
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# ACSD-64178： [!UICONTROL Edit Attribute Set]页面加载缓慢，具有数千个产品属性

ACSD-64178修补程序修复了存在数千个产品属性时&#x200B;**[!UICONTROL Edit Attribute Set]**&#x200B;页面加载缓慢的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61时，此修补程序可用。 修补程序ID为ACSD-64178。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果存在数千个产品属性，则&#x200B;**[!UICONTROL Edit Attribute Set]**&#x200B;页面加载缓慢。

<u>重现步骤</u>：

1. 创建至少4200个未分配给任何属性集的属性。
1. 在管理员侧边栏上，转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Attribute Set]**。 单击要编辑的任意属性集。

<u>预期的结果</u>：

页面会在合理的时间内加载。

<u>实际结果</u>：

加载页面需要几分钟时间。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
