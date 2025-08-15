---
title: ACSD-61534：无法使用bin/magento config：set设置设计配置，并且可以通过表单操作更改锁定的值
description: 应用ACSD-61534修补程序以修复Adobe Commerce问题，该问题导致无法使用“bin/magento config：set”命令设置设计配置，并且可以通过表单操作更改锁定的值。
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534：无法使用`bin/magento config:set`设置设计配置，并且可以通过表单操作更改锁定的值

ACSD-61534修补程序修复了无法使用`bin/magento config:set`命令设置设计配置，以及通过表单操作更改锁定值的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-61534。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法使用`bin/magento config:set`命令设置设计配置，并且可以通过表单操作更改锁定的值。 使用此修补程序，无法更新从带有`--lock-env`或`--lock-conf`的命令行工具(CLI)设置的锁定值。

<u>重现步骤</u>：

1. 使用云环境变量（如`CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`）锁定配置值。
1. 转到&#x200B;*[!UICONTROL Admin]*&#x200B;面板。
1. 转到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**。
1. 单击第二行&#x200B;**[!UICONTROL Edit]**&#x200B;附近的&#x200B;**[!UICONTROL Global/Main website]**。
1. 编辑商店视图的主题。
1. 打开HTML头。
1. 使用开发人员工具启用禁用的&#x200B;**[!UICONTROL Scripts and Style Sheets]**&#x200B;字段。
1. 更改值并保存。

<u>预期的结果</u>：

无法保存锁定的值。

<u>实际结果</u>：

表`core_config_data`包含`design/head/includes`的更新值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
