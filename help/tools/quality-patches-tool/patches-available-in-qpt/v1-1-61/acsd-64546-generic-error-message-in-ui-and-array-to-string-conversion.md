---
title: ACSD-64546：创建UPS标签期间，UI和数组到字符串的转换出现常规错误消息
description: 应用ACSD-64546修补程序以修复Adobe Commerce问题，该问题导致UI中显示一般错误消息，并且在创建UPS标签期间记录阵列到字符串转换异常。 该修补程序可确保UI和日志中显示正确的错误。
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 458371bc-4afe-4675-b090-5797e05c5b88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-64546：在创建UPS标签期间，UI中出现一般错误消息，并且&#x200B;*数组到字符串的转换*&#x200B;出现异常

ACSD-64546修补程序修复了以下问题：UI中显示一般错误消息，并且在创建UPS标签期间记录&#x200B;*阵列到字符串的转换*&#x200B;异常，从而确保在UI和日志中显示正确的错误。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61时，此修补程序可用。 修补程序ID为ACSD-64546。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

UI中显示一般错误消息，在创建UPS标签期间发生&#x200B;*数组到字符串的转换*&#x200B;异常。

<u>重现步骤</u>：

1. 使用有效地址创建客户帐户。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]**&#x200B;并添加有效的地址。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]**&#x200B;并添加有效的地址。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]**&#x200B;并配置UPS。
1. 使用[!UICONTROL UPS]下订单。
1. 从数据库中的`core_config_data`删除UPS用户ID和密码。
1. 清理配置缓存。
1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;中打开创建的订单。
1. 创建新装运。
   1. 选中&#x200B;**[!UICONTROL Create Shipping Label]**&#x200B;复选框。
   1. 单击&#x200B;**[!UICONTROL Submit shipment]**。
   1. 将产品添加到包。 指定包大小（长度、宽度和高度）。
   1. 单击&#x200B;**[!UICONTROL Save]**。

<u>预期的结果</u>：

用户界面和日志中将显示实际错误消息。

<u>实际结果</u>：

* UI中显示以下错误：
  *创建送货标签时出错。*
* *数组到字符串的转换*&#x200B;异常阻止在日志中显示或存储实际错误消息。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：
* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的升级和修补程序>应用修补程序。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：
* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
