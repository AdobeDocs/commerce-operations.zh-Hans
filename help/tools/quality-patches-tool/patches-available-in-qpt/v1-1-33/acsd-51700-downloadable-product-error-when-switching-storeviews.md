---
title: ACSD-51700：在可下载的产品编辑页面上切换商店视图时出错
description: 应用ACSD-51700补丁以修复在管理员的可下载产品编辑页面上切换商店视图时出现错误的Adobe Commerce问题。
feature: Products
role: Admin
exl-id: dd3da026-ac72-440c-8632-8a3ca27fc134
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51700：在可下载的产品编辑页面上切换商店视图时出错

ACSD-51700修补程序修复了在管理员的可下载产品编辑页面上切换存储视图时出现错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51700。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p1

## 问题

在管理员的可下载产品编辑页面上切换商店视图时出现错误。

<u>重现步骤</u>：

1. 创建可下载的产品，其名称为[!DNL SKU]，价格为。 不要添加任何链接，并保存产品。
1. 从所有存储视图切换到默认存储视图。
1. 为可下载产品创建链接并保存。
1. 从默认存储视图切换到所有存储视图。

<u>预期的结果</u>：

链接的产品可见。

<u>实际结果</u>：

将显示以下错误：

*已弃用的功能： number_format()：将null传递到类型为float的参数#1 ($num)在vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php的第228*&#x200B;行中已弃用

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
