---
title: ACSD-66084：对于订单API响应中的完全折扣项目，“row_total_incl_tax”返回接近零的残值，而不是0.00
description: 应用ACSD-66084修补程序以修复Adobe Commerce问题，该问题导致在订单API响应中，“row_total_incl_tax”返回为接近零的残值，而不是0.00（表示完全折扣的项目）。
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 01f7059e53590c4ff6602c41eb980ac7c141af33
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---


# ACSD-66084：对于订单API响应中的完全折扣项，`row_total_incl_tax`返回接近零的残值，而不是0.00

ACSD-66084修补程序修复了在订单API响应中将`row_total_incl_tax`作为近零残值返回，而不是完全折扣项目的0.00返回的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67时，此修补程序可用。 修补程序ID为ACSD-66084。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`row_total_incl_tax`在订单API响应中作为接近零的残值返回，而不是作为完全折扣项目的0.00返回。

<u>重现步骤</u>：

1. 创建具有价格和特价的产品。 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** >单击&#x200B;**[!UICONTROL Add Product]** >在&#x200B;**[!UICONTROL Price]**&#x200B;下将&#x200B;**[!UICONTROL Special Price]**&#x200B;设置为$25并将&#x200B;**[!UICONTROL Advanced Pricing]**&#x200B;设置为$16.99。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]**&#x200B;并添加20%的费率。 然后转到&#x200B;**[!UICONTROL Tax Rules]**并创建一个规则并分配
   **[!UICONTROL Taxable Goods]**&#x200B;作为产品税类。
1. 创建带100%折扣和优惠券的销售规则。 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]**&#x200B;并添加100%折扣的规则，然后使用&#x200B;**[!UICONTROL Specific Coupon]**&#x200B;并输入您的代码。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** >并配置税务设置。
1. 启用免费送货。 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]**。 将&#x200B;**[!UICONTROL Enabled]**&#x200B;设置为&#x200B;**[!UICONTROL Yes]**&#x200B;并调整设置。
1. 转到产品页面并选择&#x200B;**[!UICONTROL Add to Cart]**。 转到购物车并应用优惠券代码。
1. 在适用的税区下达订单。
1. 通过REST API生成管理员令牌(API)。
1. 通过REST API检索订单详细信息。
1. 检查响应中的`row_total_incl_tax`。

<u>预期的结果</u>：

当该项完全折扣时，`row_total_incl_tax`应返回货币适当的值，如`0.00`。

<u>实际结果</u>：

`row_total_incl_tax`返回接近零的浮点值，如`3.5527136788005e-15`，该值不适用于货币显示。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
