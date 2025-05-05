---
title: ACSD-62872：计划更新验证不正确
description: 应用ACSD-62872补丁程序，通过唯一属性验证来修复Adobe Commerce问题，该问题导致未正确验证计划的更新。
feature: Catalog Management, Admin Workspace
role: Admin, Developer
exl-id: bd0d452b-aae3-4682-8a2c-471a7f8bf132
source-git-commit: 4727a94178c642922224cb37ad5c1b2b4f6002cb
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# ACSD-62872：计划更新验证不正确

ACSD-62872修补程序修复了唯一属性验证的问题，该问题导致无法正确验证计划的更新。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56时，此修补程序可用。 修补程序ID为ACSD-62872。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>在1.1.58 QPT版本中，该修补程序在2.4.4 - 2.4.6-p8版本中被标记为已弃用。

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对自定义属性的计划更新未正确验证。

<u>重现步骤</u>：

1. 创建类别的自定义属性。
1. 导航到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**。
1. 创建新类别。
1. 在同一类别中，转到&#x200B;**[!UICONTROL Scheduled Updates]**&#x200B;部分。
1. 在以后任何时候为此类别设置新的更新。
1. 在开始计划更新之前，请尝试编辑为类别创建的计划更新。

<u>预期的结果</u>：

应该能够更新计划的更新。

<u>实际结果</u>：

引发错误： *“自定义属性”属性的值不是唯一的。 请设置唯一值并重试。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
