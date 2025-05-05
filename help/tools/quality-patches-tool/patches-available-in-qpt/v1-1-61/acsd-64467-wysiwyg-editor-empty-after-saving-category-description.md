---
title: ACSD-64467：在商店视图级别保存类别描述后，WYSIWYG编辑器为空
description: 应用ACSD-64467修补程序以修复Adobe Commerce问题，该问题导致在商店视图级别保存类别描述后，WYSIWYG编辑器显示为空。
feature: Page Content
role: Admin, Developer
source-git-commit: 4e883b3ec9b790f52dd56206539475e72bdf361d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467：在商店视图级别保存类别描述后，WYSIWYG编辑器为空

ACSD-64467修补程序修复了在商店视图级别保存类别描述后WYSIWYG编辑器显示为空的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61时，此修补程序可用。 修补程序ID为ACSD-64467。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在商店视图级别保存类别描述后，WYSIWYG编辑器显示为空。

<u>重现步骤</u>：

1. 在商店视图级别的Commerce管理员中编辑类别。
1. 取消选中类别描述旁边的&#x200B;*[!UICONTROL Use default value]*&#x200B;复选框。
1. 在WYSIWYG编辑器中输入描述。
1. 单击&#x200B;**[!UICONTROL Save]**。

<u>预期的结果</u>：

说明已保存并正确显示。

<u>实际结果</u>：

页面重新加载后，描述为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
