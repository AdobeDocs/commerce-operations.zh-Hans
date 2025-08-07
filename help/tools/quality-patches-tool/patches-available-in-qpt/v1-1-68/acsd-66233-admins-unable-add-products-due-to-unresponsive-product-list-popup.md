---
title: ACSD-66233：由于无响应的产品列表弹出窗口，管理员无法添加产品
description: 应用ACSD-66233修补程序以修复管理员无法将产品添加到类别的Adobe Commerce问题，此问题导致可视化促销器中的[!UICONTROL Add Product]弹出窗口无限期加载。
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
source-git-commit: 165b62a875747a846b15f8f86b036e67704ebc8e
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-66233：由于无响应的产品列表弹出窗口，管理员无法添加产品

ACSD-66233修补程序修复了管理员无法将产品添加到类别的问题，因为可视化促销器中的[!UICONTROL Add Product]弹出窗口会无限期加载。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-66233。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

可视化促销机中的[!UICONTROL Add Product]弹出窗口无限期加载，导致管理员无法将产品添加到类别的问题。

<u>重现步骤</u>：

1. 安装并启用清单模块。
1. 创建大量库存来源（例如，700）。
1. 创建多个库存库存（例如，12）并将库存来源分配给它们。
1. 创建一些产品并将其分配给库存来源。
1. 创建类别。
1. 展开[!UICONTROL Products in Category]部分。
1. 单击[!UICONTROL Add Product]按钮。
1. 观察包含产品列表的弹出窗口。

<u>预期的结果</u>：

产品列表会在合理的时间内加载到弹出窗口中。

<u>实际结果</u>：

弹出窗口会无限期加载，并且无法显示产品列表。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
