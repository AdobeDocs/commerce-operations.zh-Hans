---
title: ACSD-66118：如果更新[!UICONTROL Store View Code]时未刷新[!UICONTROL Design Configuration]，则清除[!UICONTROL Configuration Cache]设置
description: 应用ACSD-66118修补程序以修复Adobe Commerce问题，该问题导致如果[!UICONTROL Store View Code]未正确刷新，则更新[!UICONTROL Design Configuration]将清除[!UICONTROL Configuration Cache]（主题和自定义设置）。
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
exl-id: ecfdff54-99e0-4dbe-a0bb-80f60aafc7b6
source-git-commit: 468c780f355c99cf06d557e530e81c414a01961e
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ACSD-66118：如果更新&#x200B;**[!UICONTROL Store View Code]**&#x200B;时未刷新&#x200B;**[!UICONTROL Design Configuration]**，则清除&#x200B;**[!UICONTROL Configuration Cache]**&#x200B;设置

ACSD-66118修补程序修复了以下问题：如果&#x200B;**[!UICONTROL Store View Code]**&#x200B;未刷新，则更新&#x200B;**[!UICONTROL Design Configuration]**&#x200B;将清除&#x200B;**[!UICONTROL Configuration Cache]**&#x200B;设置。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67时，此修补程序可用。 修补程序ID为ACSD-66118。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果未刷新&#x200B;**[!UICONTROL Design Configuration]**，则在更新&#x200B;**[!UICONTROL Store View Code]**&#x200B;字段时会清除&#x200B;**[!UICONTROL Configuration Cache]**&#x200B;设置（如主题和自定义设置）。

<u>重现步骤</u>：

1. 登录到&#x200B;**[!UICONTROL Admin]**&#x200B;面板。
2. 导航到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**。
3. 编辑具有在&#x200B;**[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]**&#x200B;中配置的自定义主题的存储区视图。
4. 更改&#x200B;**[!UICONTROL Code]**&#x200B;字段（例如，从`storeview_1`更改为`storeview_main`）。
5. 单击&#x200B;**[!UICONTROL Save Store View]**&#x200B;保存更改。
6. 刷新或重新打开已更新&#x200B;**[!UICONTROL Content]**&#x200B;的&#x200B;*[!UICONTROL Design]* > **[!UICONTROL Configuration]** > **[!UICONTROL Store View]**&#x200B;页面，将不选择主题。

<u>预期的结果</u>：

更新&#x200B;**[!UICONTROL Store View Code]**&#x200B;后，**[!UICONTROL Design Configuration]**（包括主题和自定义设置）应保持不变。

<u>实际结果</u>：

**[!UICONTROL Design Configuration]**&#x200B;已清除。 主题将还原为默认主题，并且自定义设置将丢失。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
