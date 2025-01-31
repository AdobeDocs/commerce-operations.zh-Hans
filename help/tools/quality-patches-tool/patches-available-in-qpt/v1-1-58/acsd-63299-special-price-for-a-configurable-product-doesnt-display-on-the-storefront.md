---
title: ACSD-63299：店面不显示可配置产品的特殊价格
description: 应用ACSD-63299修补程序以修复Adobe Commerce问题，该问题导致特殊价格属性不再影响可配置产品的特殊价格的显示。
feature: Catalog Management
Role: Admin, Developer
source-git-commit: 238d3fa6d7729f729aeb79c98ae28db331ad7509
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299：店面不显示可配置产品的特殊价格

ACSD-63299修补程序修复了特殊价格属性不再影响可配置产品的特殊价格显示的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-63299。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在[!DNL Adobe Commerce]中，更改特殊价格属性的&#x200B;*在产品列表中使用*&#x200B;的值不再影响可配置产品的特殊价格的显示方式。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]**。
1. 查找&#x200B;***[!UICONTROL special_price]***&#x200B;属性并导航到&#x200B;**[!UICONTROL Storefront Properties]**。
1. 将&#x200B;***[!UICONTROL Used in Product Listing]***&#x200B;更改为***[!UICONTROL No]***。
1. 创建一个带有一个子项的可配置产品：
   * 名称和SKU：测试
   * 价格：159.00美元
   * 根据颜色生成选项。 添加新颜色：蓝色
   * 保存
1. 打开子产品，然后按照以下步骤操作：
   * 在&#x200B;**[!UICONTROL Advanced Pricing]**&#x200B;中将特价设置为$99.90
   * 将[!UICONTROL Visibility]更改为&#x200B;**[!UICONTROL Catalog, Search]**。
1. 打开简单产品页，并确认特殊价格可见。
1. 打开可配置的产品页面。
1. 选择蓝色产品。

<u>预期的结果</u>：

特殊价格的显示方式与简单产品相同。

<u>实际结果</u>：

1. 选择可配置产品时，将显示完整价格。
1. 低至……*的部分*&#x200B;与实际价格($99.90 + $59.10 = $159.00)不匹配。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
