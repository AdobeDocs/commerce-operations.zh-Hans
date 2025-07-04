---
title: ACSD-58163： [!UICONTROL Cart Price Rule]不应用来自匹配[!UICONTROL Customer Segment]购物车（不含优惠券代码）的折扣
description: 应用ACSD-58163修补程序以修复Adobe Commerce问题，该问题导致[!UICONTROL Cart Price Rule]不通过无优惠券代码的匹配[!UICONTROL Customer Segment]购物车为访客应用折扣。
feature: Products
role: Admin, Developer
exl-id: 209a50f7-32d9-40e9-bfd5-4658e4ca392d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-58163： [!UICONTROL Cart Price Rule]不应用来自匹配[!UICONTROL Customer Segment]购物车（不含优惠券代码）的折扣

ACSD-58163修补程序修复了[!UICONTROL Cart Price Rule]不应用来自匹配[!UICONTROL Customer Segment]购物车（不含优惠券代码）的折扣的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49时，此修补程序可用。 修补程序ID为ACSD-58163。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!UICONTROL Cart Price Rule]不为来自匹配[!UICONTROL Customer Segment]购物车（不含优惠券代码）的访客应用折扣。

<u>重现步骤</u>：

1. 创建客户区段：
   * 对于访客。
   * 条件是在购物车中拥有一种产品。

1. 创建&#x200B;*[!UICONTROL Cart Price Rule]*：
   * 没有优惠券代码。
   * 带有与访客客户区段匹配的条件。

1. 创建一个简单的产品。
1. 作为客人开门营业吧。
1. 将一个简单产品添加到购物车。
1. 转到购物车。

<u>预期的结果</u>：

已应用&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;折扣。

<u>实际结果</u>：

未应用&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;折扣。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
