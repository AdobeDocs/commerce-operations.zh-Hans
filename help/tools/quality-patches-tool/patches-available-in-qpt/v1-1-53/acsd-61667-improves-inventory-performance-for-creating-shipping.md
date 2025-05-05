---
title: ACSD-61667：提高库存性能以创建发运
description: 应用ACSD-60584修补程序以提高库存性能，以便在存在许多店内装货来源的情况下创建装运。
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
source-git-commit: c32684a09e4a99733feb198b1d353b090c68a7f5
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667：提高库存性能以创建发运

ACSD-61667修补程序修复了在为多个来源启用[[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/inventory/introduction)（以前为MSI）接收存储时商家无法发送订单的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53时，此修补程序可用。 修补程序ID为ACSD-61667。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用MSI提货存储后，您将无法发运具有多个来源的订单。 此修补程序提高了库存性能，以便在存在许多店内取货来源时能够创建送货流程。

<u>先决条件：</u>：

已安装和启用Adobe Commerce清单模块。

<u>重现步骤</u>：

1. 创建超过&#x200B;*10*&#x200B;个源并启用其接收位置。
1. 已在&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**&#x200B;下启用收取商店。
1. 创建大量装货订单。
1. 转到&#x200B;**[!UICONTROL Admin login]**&#x200B;并选择&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]**。
1. 筛选并检查待处理订单。
1. 单击&#x200B;**[!UICONTROL Ship]**。

<u>预期的结果</u>：

装运页面按预期加载。

<u>实际结果</u>：

您收到&#x200B;*503最大执行超时*&#x200B;错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
