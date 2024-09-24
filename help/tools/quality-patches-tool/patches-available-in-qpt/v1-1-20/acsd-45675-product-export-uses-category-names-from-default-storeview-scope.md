---
title: 'ACSD-45675：产品导出使用默认商店视图范围内的类别名称'
description: ACSD-45675修补程序修复了产品导出使用默认商店视图范围内的类别名称的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20后，即可使用此修补程序。 修补程序ID为ACSD-45675。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-45675：产品导出使用默认商店视图范围内的类别名称

ACSD-45675修补程序修复了产品导出使用默认商店视图范围内的类别名称的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20时，此修补程序可用。 修补程序ID为ACSD-45675。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品导出使用默认商店视图范围内的类别名称。

<u>重现步骤</u>：

1. 在主存储中创建自定义存储视图&#x200B;**[!UICONTROL Thai]**。
1. 将&#x200B;**[!UICONTROL Thai]**&#x200B;设置为主网站的默认商店视图。
1. 在&#x200B;**[!UICONTROL Default Category]**&#x200B;下创建以下类别结构：

   *[!UICONTROL Default category/Tea/Black]*

1. 选择类别&#x200B;**[!UICONTROL Tea]**&#x200B;并将&#x200B;**[!UICONTROL Scope]**&#x200B;更改为&#x200B;**[!UICONTROL Thai]**。
1. 将&#x200B;**[!UICONTROL Category Name]**&#x200B;设置为&#x200B;**[!UICONTROL ชาดำ]**。
1. 创建简单产品&#x200B;**[!UICONTROL SP001]**&#x200B;并分配类别&#x200B;**[!UICONTROL Black]**。
1. 确保cron不运行。
1. 执行产品导出。 按SKU筛选并选择&#x200B;**[!UICONTROL SP001]**。
1. 检查导出的CSV中的&#x200B;**[!UICONTROL categories]**&#x200B;列。

<u>预期的结果</u>：

由于在导出期间未选择存储，因此您应获得如下类别路径： *[!UICONTROL Default Category/Tea/Black]*。

<u>实际结果</u>：

类别路径具有混合语言： *[!UICONTROL Default Category/ชาดำ/Black]*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tools] > Quality Patches Tool指南中的用法](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关[!DNL QPT]中其他可用修补程序的信息，请参阅Quality Patches Tool指南中的 [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中的[Patches。
