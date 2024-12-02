---
title: ACSD-61133： 'sales_clean_quotes' cron从未批准的采购订单中删除报价
description: 应用ACSD-61133修补程序以修复Adobe Commerce问题，该问题导致“sales_clean_quotes”cron从未批准的采购订单中删除报价。
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
source-git-commit: 05f94eb45fe6ec08b9e9f9d3bb7ad3c6fb8d5445
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133： `sales_clean_quotes` cron从未批准的采购订单中删除报价

ACSD-61133修补程序修复了`sales_clean_quotes` cron从未批准的采购订单中删除报价的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.53时，此修补程序可用。 修补程序ID为ACSD-61133。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4-p5 - 2.4.4-p11、2.4.5-p4 - 2.4.5-p10和2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`sales_clean_quotes` cron会从未批准的采购订单中删除报价。 无法将&#x200B;*[B2B采购订单]*&#x200B;转换为与采购订单关联的报价单，因为cron将删除该订单。

<u>先决条件</u>：

已安装和启用Adobe Commerce [!UICONTROL B2B]模块。

<u>重现步骤</u>：

1. 启用&#x200B;*[!UICONTROL B2B Purchase Order]*&#x200B;功能。
1. 创建公司。
1. 创建一个&#x200B;*[!UICONTROL Purchase Order]*。
1. 等待报价过期并被cron删除。 可以使用&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]**&#x200B;设置报价过期时间。
1. 通过&#x200B;*[!UICONTROL My Purchase Order in Customer Dashboard]*&#x200B;或通过[!DNL GraphQL] `placeOrderForPurchaseOrder`突变将&#x200B;*[!UICONTROL Purchase Order]*&#x200B;转换为订单。

<u>预期的结果</u>：

与活动&#x200B;*[!UICONTROL Purchase Order]*&#x200B;关联的报价未被cron删除为已过期。 已成功在店面或通过[!DNL GraphQL]下订单。

<u>实际结果</u>：

未下订单，店面显示错误或在[!DNL GraphQL]响应中返回。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
