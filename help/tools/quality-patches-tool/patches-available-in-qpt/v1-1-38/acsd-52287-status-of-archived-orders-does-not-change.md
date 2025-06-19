---
title: ACSD-52287：已存档订单的状态不会更改
description: 应用ACSD-52287修补程序以修复在提交贷项通知单后，网格上存档订单的状态不会从*已完成*更改为*已关闭*的Adobe Commerce问题。
feature: Orders, Checkout
role: Admin, Developer
exl-id: 012f49ba-fdc1-4e1e-87fe-7b9c661f231b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-52287：已存档订单的状态不会更改

ACSD-52287修补程序修复了在提交贷项通知单后，已存档订单的状态不会从网格上的&#x200B;*已完成*&#x200B;更改为&#x200B;*已关闭*&#x200B;的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.38时，此修补程序可用。 修补程序ID为ACSD-52287。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

提交贷项通知单后，已存档订单的状态不会从网格上的&#x200B;*已完成*&#x200B;更改为&#x200B;*已关闭*。

<u>重现步骤</u>：

1. 配置&#x200B;*[!UICONTROL Asynchronous Indexing]*。
   * 在管理员侧边栏上，转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**。
   * 在左侧面板中，展开&#x200B;**[!UICONTROL Advanced]**&#x200B;部分并在下面选择&#x200B;**[!UICONTROL Developer]**。
   * 展开&#x200B;**[!UICONTROL Grid Settings]**&#x200B;部分。
   * 将&#x200B;*[!UICONTROL Asynchronous indexing]*&#x200B;设置为&#x200B;*是*。
   * 单击&#x200B;**[!UICONTROL Save Config]**。
1. 配置&#x200B;*[!UICONTROL Order Archive]*。
   * 在管理员侧边栏上，转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**。
   * 在左侧面板中，展开&#x200B;**[!UICONTROL Sales]**&#x200B;部分并在下面选择&#x200B;**[!UICONTROL Sales]**。
   * 展开&#x200B;**[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]**&#x200B;部分。
   * 将&#x200B;*[!UICONTROL Enable Archiving]*&#x200B;设置为&#x200B;*是* （将其余配置保留为默认值）。
   * 单击&#x200B;**[!UICONTROL Save Config]**。
1. 在前端下订单。
1. 运行[!DNL cron]以便显示在&#x200B;*[!UICONTROL Admin Order Grid]*&#x200B;中。
1. 开票并发送订单，以将订单状态更新为&#x200B;*完成*。
1. 运行[!DNL cron]以使用最新的订单状态更新&#x200B;*[!UICONTROL Sales Order Grid]*。
1. 存档订单。
1. 转到&#x200B;*[!UICONTROL Archived order grid]*。
1. 打开已存档的订单并通过创建[!UICONTROL Credit Memo]以使[!UICONTROL Order status]： *已关闭*&#x200B;来离线退款。
1. 运行[!DNL cron]几次。
1. 检查&#x200B;*[!UICONTROL Archived order grid]*&#x200B;的新订单状态。

<u>预期的结果</u>：

订单显示为&#x200B;*已关闭*。

<u>实际结果</u>：

顺序显示为&#x200B;*完成*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
