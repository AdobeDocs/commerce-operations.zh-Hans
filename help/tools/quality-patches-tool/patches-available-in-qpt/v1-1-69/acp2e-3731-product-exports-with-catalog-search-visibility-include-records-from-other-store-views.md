---
title: ACP2E-3731：具有[!UICONTROL Catalog, Search]可见性的产品导出包括来自其他商店视图的记录
description: 应用ACP2E-3731修补程序以修复Adobe Commerce，该修补程序将可见性筛选器设置为[!UICONTROL Catalog, Search]的产品导出由于存储范围的属性变化而在多存储设置中包含不正确的行。
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731：具有[!UICONTROL Catalog, Search]可见性的产品导出包括来自其他商店视图的记录

ACP2E-3731修补程序修复了可见性为&#x200B;*[!UICONTROL Catalog, Search]*&#x200B;的产品导出错误地包含多商店环境中其他商店视图中的记录的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACP2E-3731。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p9

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当可见性过滤器在多商店设置中设置为&#x200B;*[!UICONTROL Catalog, Search]*&#x200B;时，由于商店范围的属性变化，产品导出包含不正确的行。

<u>重现步骤</u>：

1. 在“管理员”面板中，转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**&#x200B;以创建其他网站、商店和商店视图。
1. 转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]**。 单击&#x200B;**[!UICONTROL Add Attribute Set]**&#x200B;创建属性。 将&#x200B;**[!UICONTROL Based On]**&#x200B;设置为&#x200B;*默认值*。
1. 创建产品并将其分配给主网站和辅助网站。
1. 为新创建的属性设置文本值，并将&#x200B;**[!UICONTROL Scope]**&#x200B;设置为&#x200B;*所有存储视图*。
1. 将范围更改为辅助存储视图，并使用不同的值更新属性。
1. 将范围更改为默认商店视图和辅助商店视图，然后将产品可见性设置为&#x200B;*不可单独显示*。
1. 转到&#x200B;**[!UICONTROL System]** > **[!UICONTROL Export]**，然后从下拉菜单中选择&#x200B;*产品*。
1. 设置&#x200B;**[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]*&#x200B;的筛选器，然后单击&#x200B;**[!UICONTROL Continue]**。
1. 运行以下命令以处理导出：

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. 检查导出的文件。

<u>预期的结果</u>：

仅导出过滤的记录。

<u>实际结果</u>：

导出的文件包含用于次存储视图的行，该行与导出期间设置的筛选条件不匹配。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
