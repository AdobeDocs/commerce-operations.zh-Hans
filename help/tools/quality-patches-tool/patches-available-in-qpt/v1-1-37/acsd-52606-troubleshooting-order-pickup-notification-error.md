---
title: ACSD-52606：用户单击“Notify Order is Ready for Pickup”（通知订单准备好提货）时显示的错误消息
description: 应用ACSD-52606修补程序以修复当用户单击**[!UICONTROL Notify Order is Ready for Pickup]**时显示错误消息的Adobe Commerce问题。
feature: Orders, User Account
role: Admin, Developer
exl-id: d0b5a7a6-0d32-4019-8f28-60722fce1a99
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-52606：用户单击“Notify Order is Ready for Pickup”（通知订单准备好提货）时显示的错误消息

ACSD-52606修补程序修复了以下问题：用户单击&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;时，显示错误消息&#x200B;*您的订单未做好接收准备*。 安装[!DNL Quality Patches Tool (QPT)] 1.1.37时，此修补程序可用。 修补程序ID为ACSD-52606。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当用户单击&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;时，屏幕上将显示错误消息&#x200B;*您的订单未准备好取货*。

<u>先决条件</u>：

清单模块已安装。

<u>重现步骤</u>：

1. 安装新实例。
1. 创建新的源和库存。
1. 将新源分配给默认网站。
1. 为新创建的源启用取车地点。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**&#x200B;并启用&#x200B;**[!UICONTROL In-Store Delivery]**。
1. 为所有库存和&#x200B;*[!UICONTROL Manage Stock = No]*&#x200B;创建具有&#x200B;*QTY=0*&#x200B;的&#x200B;*In Stock*&#x200B;简单产品，并将其分配给两个来源。
1. 从前端使用上一步中创建的产品创建订单，选择&#x200B;*[!UICONTROL In-Store Pickup]*&#x200B;作为交货方式。
1. 在“管理员”中，转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**。
1. 单击&#x200B;**[!UICONTROL Notify order is ready for pickup]**。

<u>预期的结果</u>：

您会收到无错误的通知。

<u>实际结果</u>：

您收到以下错误消息： *您的订单未准备好接送*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
