---
title: ACSD-63062：使用多个重叠规则计算的购物车折扣不正确
description: 应用ACSD-63062补丁以修复在应用多个重叠规则时购物车折扣计算不正确的Adobe Commerce问题。
feature: Price Rules
role: Admin, Developer
source-git-commit: 06fbdf730c670065e3105c62ae9604307b296a45
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062：使用多个重叠规则计算的购物车折扣不正确

ACSD-63062修补程序修复了在应用多个重叠规则时发生错误的购物车折扣计算的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56时，此修补程序可用。 修补程序ID为ACSD-63062。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

应用多个重叠规则时，购物车折扣计算不正确。

<u>重现步骤</u>：

1. 使用示例数据安装新实例。
1. 创建三个简单的产品：

   * 简单1:1080美元
   * 简单2:260美元
   * 简单3:280美元

1. 按如下方式创建四个&#x200B;*[!UICONTROL Cart Price Rules]*：

   * 规则1：

      * *[!UICONTROL Priority]*： 100
      * *[!UICONTROL Conditions]*&#x200B;选项卡：如果总数量等于或大于3，则使用简单2 ($280)产品
      * *[!UICONTROL Actions]*&#x200B;选项卡： SKU很简单2
      * *[!UICONTROL Fixed Amount Discount]*： $80

   * 规则2：

      * *[!UICONTROL Priority]*： 200
      * *[!UICONTROL Actions]*&#x200B;选项卡： SKU很简单2
      * *[!UICONTROL Percentage of Product Price Discount]*： 20%

   * 第3条：

      * *[!UICONTROL Priority]*： 300
      * *[!UICONTROL Conditions]*&#x200B;选项卡：小计等于或大于$1000
      * 整个购物车的&#x200B;*[!UICONTROL Fixed Amount Discount]*： $100

   * 第4条：

      * *[!UICONTROL Priority]*： 400
      * *[!UICONTROL Conditions]*&#x200B;选项卡：如果总数量等于或大于2，则使用简单1 ($1080)产品
      * *[!UICONTROL Actions]*&#x200B;选项卡： SKU很简单1
      * 整个购物车的&#x200B;*[!UICONTROL Fixed Amount Discount]*： $960

1. 转到店面，将以下具有给定数量的产品添加到购物车：

   * 简单1 = 2
   * 简单2 = 1
   * 简单3 = 3

1. 检查购物车。

<u>预期的结果</u>：

适用的折扣为$1352。

<u>实际结果</u>：

适用的折扣为1525.33美元。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
