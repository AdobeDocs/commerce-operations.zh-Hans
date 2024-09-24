---
title: 'ACSD-48813：搜索未根据属性的搜索权重显示相关结果'
description: Adobe Commerce应用ACSD-48813修补程序以修复以下问题：根据属性的搜索权重，搜索未显示相关结果。
feature: Admin Workspace, Attributes, Search
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48813：搜索未根据属性的搜索权重显示相关结果

ACSD-48813修补程序修复了搜索未根据属性的搜索权重显示相关结果的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-48813。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

搜索未根据属性的搜索权重显示相关结果。

<u>重现步骤</u>：

1. 使用示例数据安装Adobe Commerce。
1. 将搜索引擎设置为[!DNL Elasticsearch]。
1. 以管理员身份登录。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**。
1. 打开&#x200B;*name*&#x200B;属性。
1. 打开店面&#x200B;*[!UICONTROL Properties]*&#x200B;选项卡。
1. 从下拉值中选择[!UICONTROL Search Weight] = *10*。
1. 单击&#x200B;**[!UICONTROL Save Attribute]**。
1. 现在打开店面并搜索单词&#x200B;*Back*。

<u>预期的结果</u>：

返回搜索结果顶部的背包产品。

<u>实际结果</u>：

在搜索结果中会返回背包产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
