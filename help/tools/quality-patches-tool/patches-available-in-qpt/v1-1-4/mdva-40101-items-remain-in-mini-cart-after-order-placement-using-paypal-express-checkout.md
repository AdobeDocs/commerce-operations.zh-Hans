---
title: 'MDVA-40101：下单后商品仍为迷你购物车PayPal Express结帐'
description: MDVA-40101修补程序修复了在使用PayPal Express结帐成功下订单后无法从微型购物车中删除项目的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4后，即可使用此修补程序。 修补程序ID为MDVA-40101。 请注意，Adobe Commerce 2.4.0中已修复此问题。
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-40101：下单后商品仍为迷你购物车PayPal Express结帐

MDVA-40101修补程序修复了在使用PayPal Express结帐成功下订单后无法从微型购物车中删除项目的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4时，此修补程序可用。 修补程序ID为MDVA-40101。 请注意，Adobe Commerce 2.4.0中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.3.7

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使使用PayPal Express结帐成功下订单，商品仍会保留在迷你购物车中。

<u>重现步骤</u>：

在浏览器中，以无痕模式使用PayPal Express Checkout下订单。

<u>预期的结果</u>：

成功完成订单后，迷你购物车应为空。

<u>实际结果</u>：

* 成功页面显示一个空的迷你购物车。
* 所有其他页面显示包含已购项目的迷你购物车。
* 单击购物车链接会将您重定向到空的购物车页面。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-)中可用的[修补程序部分。
