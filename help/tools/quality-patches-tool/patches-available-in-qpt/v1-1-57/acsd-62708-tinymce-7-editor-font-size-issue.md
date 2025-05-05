---
title: ACSD-62708：管理面板中的 [!DNL TinyMCE] 7编辑器字体大小显示PT
description: 应用ACSD-62708修补程序以修复Adobe Commerce问题，该问题导致管理员中的 [!DNL TinyMCE] 7编辑器字体大小显示为PT，而不是PX。 现在，您还可以以PX而不是PT设置字体大小。
feature: Admin Workspace
role: Admin, Developer
source-git-commit: ecb04a058e858580dfbc7a1edcd319423be9eeaa
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# ACSD-62708：管理面板中的[!DNL TinyMCE] 7编辑器字体大小显示PT

ACSD-62708修补程序解决了管理面板中的[!DNL TinyMCE] 7编辑器字体大小以PT而不是PX显示的问题。 此修补程序允许您以PX为单位设置字体大小。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-62708。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p11、2.4.5-p10、2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理面板中的[!DNL TinyMCE] 7编辑器以PT格式显示字体大小，而不是PX格式。

<u>重现步骤</u>：

1. 在管理面板中打开产品编辑页面。
1. 展开[!UICONTROL Content]部分。
1. 检查[!DNL TinyMCE]编辑器中的字体控件。

<u>预期的结果</u>：

字体大小应以PX为单位。

<u>实际结果</u>：

字体大小为PT。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
