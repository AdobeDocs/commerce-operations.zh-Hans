---
title: MDVA-40399：无法通过API同时创建同一订单的部分发票
description: MDVA-40399修补程序修复了无法通过Rest API同时创建同一订单的部分发票的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4后，即可使用此修补程序。 修补程序ID为MDVA-40399。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: REST, Invoices, Orders
role: Admin
exl-id: aa400a15-57b9-4f80-a49f-f4680b7e4705
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40399：无法通过API同时创建同一订单的部分发票

MDVA-40399修补程序修复了无法通过Rest API同时创建同一订单的部分发票的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4时，此修补程序可用。 修补程序ID为MDVA-40399。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

不能使用Rest API同时创建相同订单的部分发票。

<u>先决条件</u>：

一种具有至少两个变体的可配置产品。

<u>重现步骤</u>：

1. 将可配置产品的两个变体添加到购物车。
1. 下订单。
1. 通过Rest API同时为订单创建两张发票。

<u>预期的结果</u>：

* 必须成功创建这两张发票。
* 应在`sales_order_item`表中为这两张发票更新`qty_invoiced`。
* 这两种产品都应该有开票数量。

<u>实际结果</u>：

* 已成功创建这两张发票。
* 未针对`sales_order_item`表中的发票之一更新`qty_invoiced`。
* 在管理员的&#x200B;**订单视图**&#x200B;页面中，只显示一个产品的发票数量。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中可用的修补程序部分。
