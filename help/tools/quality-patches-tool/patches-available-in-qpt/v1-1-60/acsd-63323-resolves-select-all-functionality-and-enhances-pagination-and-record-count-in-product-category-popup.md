---
title: ACSD-63323：解析[!UICONTROL Select All]功能并增强产品类别弹出窗口中的分页和记录计数
description: 应用ACSD-63323修补程序以修复将产品添加到类别时，[!UICONTROL Select All]选项不起作用的Adobe Commerce问题。 此外，当通过弹出网格将产品添加到类别时，它还可确保分页和记录计数标签正常工作。
feature: Products
role: Admin, Developer
exl-id: 96e318fd-f1dd-4b15-b171-78ae1c8e4e0d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-63323：解析[!UICONTROL Select All]功能并增强产品类别弹出窗口中的分页和记录计数

ACSD-63323修补程序修复了在将产品添加到类别时，**[!UICONTROL Select All]**&#x200B;选项不起作用的问题。 此外，当通过弹出网格将产品添加到类别时，它还可确保分页和记录计数标签正常工作。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60时，此修补程序可用。 修补程序ID为ACSD-63323。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了&#x200B;**[!UICONTROL Select All]**&#x200B;选项在“管理员”>“**[!UICONTROL Categories]**”>“选择类别”>“**[!UICONTROL Products in Category]**”>“**[!UICONTROL Add Products]**”中无效的问题。 通过弹出网格将产品添加到类别时，它还有助于分页和记录计数标签正常工作。


<u>重现步骤</u>：

1. 使用以下命令生成&#x200B;*1200*&#x200B;产品：

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. 打开&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;并查看产品数：找到了&#x200B;*1200*&#x200B;条记录。
1. 打开默认类别> **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**。
1. 单击&#x200B;**[!UICONTROL Assign]** > **[!UICONTROL Select All]**。
1. 将页面上的产品数更改为值= *5*。


**预期的结果**：

*消息应为：找到1200条记录（已选择1200条）*

**实际结果**：

* 分页不起作用。
* 显示错误消息：找到&#x200B;*5*&#x200B;条记录（已选择&#x200B;*20*&#x200B;条）

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
