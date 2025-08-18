---
title: AC-15223：Storefront页面显示切换存储后缓存的内容
description: 应用AC-15223修补程序以修复以下Adobe Commerce问题：在切换后，将从缓存中提供页面，但存储未按预期切换。
feature: Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: ea3584e180acad1765f5b8105c45170725c71269
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# AC-15223：Storefront页面显示切换存储后缓存的内容

AC-15223修补程序修复了以下问题：在切换存储后，由于存储切换器无法正常工作，因此会从缓存中提供页面。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为AC-15223。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在切换存储之后，从缓存中提供页面（存储切换器无法正常工作）。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**。
2. 创建新的商店视图。
3. 转到店面，尝试切换店面视图。

<u>预期的结果</u>：

已成功切换商店视图。

<u>实际结果</u>：

在从后端清理缓存之前，不会更改标头中的存储视图名称。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
