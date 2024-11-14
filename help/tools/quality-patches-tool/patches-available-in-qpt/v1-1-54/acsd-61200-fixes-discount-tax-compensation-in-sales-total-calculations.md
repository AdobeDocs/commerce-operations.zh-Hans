---
title: “ACSD-61200：修复销售总额计算中的折扣税补偿”
description: 应用ACSD-61200修补程序以修复销售总额计算中缺少*[!UICONTROL Discount Tax Compensation Amount]*和*[!UICONTROL Shipping Discount Tax Compensation Amount]*而导致销售订单数据与优惠券报表数据不一致的Adobe Commerce问题。
feature: Reporting, Taxes
role: Admin, Developer
source-git-commit: 61259d8e059cd813a84907e4baef873b2cc8cad0
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200：修复销售总额计算中的折扣税补偿

ACSD-61200修补程序修复了以下问题：*[!UICONTROL Total Amount]*&#x200B;和&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;计算中缺少&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;和&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*，从而导致销售订单数据与优惠券报表数据之间存在差异。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54时，此修补程序可用。 修补程序ID为ACSD-61200。 请注意，该问题计划在Adobe Commerce版本2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

- Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

- Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于销售总额计算中缺少&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;和&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*，导致销售订单和优惠券报表数据不准确。

<u>重现步骤</u>：

1. 创建[!UICONTROL Tax Zone]和[!UICONTROL Tax Rule]。
1. 设置以下税务配置：
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. 更新订单、发票和贷项通知单的以下显示设置：
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. 创建包含优惠券的[!UICONTROL Cart Price Rule]，享有10%的折扣。
1. 使用优惠券完成订单，并生成发票和发运。
1. 转到&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]**&#x200B;并生成报告。
1. 比较订单摘要和报表中的数据。

<u>预期的结果</u>：

*[!UICONTROL Total Amount]*&#x200B;和&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;计算包括&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;和&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*，将订单摘要与报表数据进行匹配。

<u>实际结果</u>：

销售订单数据和优惠券报表数据不匹配，因为计算中缺少&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;和&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

- Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
- 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

[[!DNL Quality Patches Tool] 已发布：“工具”指南中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
