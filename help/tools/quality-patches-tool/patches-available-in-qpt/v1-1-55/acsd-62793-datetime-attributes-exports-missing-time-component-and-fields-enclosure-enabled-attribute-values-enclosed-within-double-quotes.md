---
title: ACSD-62793：导出中的日期时间属性缺少时间组件。 此外，如果启用**[!UICONTROL Fields Enclosure]**，属性值会用双引号括起来
description: 应用ACSD-62793修补程序以修复导出数据中的日期时间属性缺少时间组件的Adobe Commerce问题。 此外，如果启用了**[!UICONTROL Fields Enclosure]**，则*additional_attributes*列中的属性值将用双引号括起来。
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
exl-id: 340dcc84-dcb8-40ed-b2ab-2d950d1dd1ca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-62793：导出中的日期时间属性缺少时间组件。 此外，如果启用&#x200B;**[!UICONTROL Fields Enclosure]**，属性值将用双引号括起来

ACSD-62793修补程序修复了导出数据中的日期时间属性缺少时间组件的问题。 此外，如果启用了&#x200B;**[!UICONTROL Fields Enclosure]**，则&#x200B;*additional_attributes*&#x200B;列中的属性值将用双引号括起来。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-62793。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

导出数据中的日期时间属性不包括时间组件。 此外，如果启用了&#x200B;**[!UICONTROL Fields Enclosure]**，则&#x200B;*additional_attributes*&#x200B;列中的属性值将用双引号括起来。

<u>重现步骤</u>：

1. 创建具有&#x200B;**[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]**&#x200B;的产品属性。
1. 将属性分配给&#x200B;**[!UICONTROL Default]**&#x200B;属性集。
1. 为新属性创建一个具有日期和时间值的简单产品。
1. 从&#x200B;**[!UICONTROL System]** > *数据传输* > **[!UICONTROL Export]**&#x200B;将产品导出到CSV文件。
1. 检查&#x200B;*additional_attributes*&#x200B;列中的属性值。 它只有日期部分，但没有时间。
1. 更新属性值以使用时间，例如“08/10/22， 3:20 PM”。
1. 导入CSV文件。
1. 检查&#x200B;*catalog_product_entity_datetime*&#x200B;表。

<u>预期的结果</u>：

正确导出和导入日期和时间。

<u>实际结果</u>：

仅导出和导入日期部分。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
