---
title: 'ACSD-49706：未选择任何值时为可视样本属性保存的默认值'
description: 应用ACSD-49706修补程序以修复在未选择任何值时为可视样本属性保存默认值的Adobe Commerce问题。
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-49706：未选择任何值时为可视样本属性保存的默认值

ACSD-49706修补程序修复了在未选择任何值时为可视样本属性保存默认值的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-49706。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果未选择任何值，则会为可视样本属性保存默认值。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**。
1. 单击&#x200B;**[!UICONTROL Add New Attribute]**。
1. 填写字段。

   * 例如，选择输入类型&#x200B;*[!UICONTROL Visual Swatch]*，然后添加多个选项（如&#x200B;*Red*、*Green*）。 请确保选择其中一个选项作为默认选项。
   * 单击&#x200B;**[!UICONTROL Save Attribute]**。

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**。
1. 编辑&#x200B;*[!UICONTROL Default]*&#x200B;属性集。
1. 将&#x200B;*[!UICONTROL New Attribute]*&#x200B;从列&#x200B;*[!UICONTROL Unassigned Attributes]*&#x200B;移至中间列中的&#x200B;*[!UICONTROL Product Details]*&#x200B;文件夹。

   * 单击&#x200B;**[!UICONTROL Save]**。

1. 使用&#x200B;*[!UICONTROL Default]*&#x200B;属性集创建新产品。

   * 将&#x200B;*[!UICONTROL New Attribute]*&#x200B;保留为空并保存。

1. 保存后，*[!UICONTROL New Attribute]*&#x200B;中将显示一个值。

<u>预期的结果</u>：

默认情况下没有分配给&#x200B;*[!UICONTROL New Attribute]*&#x200B;的值。

<u>实际结果</u>：

在保存产品时，默认值将应用于属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。