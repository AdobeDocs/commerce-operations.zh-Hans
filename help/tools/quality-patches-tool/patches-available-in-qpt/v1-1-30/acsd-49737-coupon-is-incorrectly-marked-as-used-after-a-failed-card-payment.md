---
title: ACSD-49737：在信用卡付款失败后，错误地标记为使用了优惠券
description: 应用ACSD-49737修补程序以修复在失败信用卡支付后错误地标记为使用优惠券的Adobe Commerce问题。
feature: Orders, Payments
role: Admin
exl-id: 09060026-8d64-49f6-a85a-3230a52030fb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49737：在信用卡付款失败后，优惠券被错误地标记为&#x200B;*已使用*

ACSD-49737修补程序修复了在支付卡失败后，优惠券被错误地标记为&#x200B;*已使用*&#x200B;的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30时，此修补程序可用。 修补程序ID为ACSD-49737。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在信用卡付款失败后，优惠券被错误地标记为&#x200B;*已使用*。

<u>先决条件</u>：

1. 配置&#x200B;**[!UICONTROL Braintree sandbox payment]**&#x200B;方法。
1. 确保&#x200B;[*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en)使用者已设置并正在运行。

<u>重现步骤</u>：

1. 使用自动生成的优惠券代码创建&#x200B;**[!UICONTROL Cart Price Rule]**。
1. 以客户身份登录。
1. 将产品添加到购物车。
1. 应用自动生成的优惠券代码。
1. 尝试以失败的付款下订单。
1. 检查&#x200B;**[!UICONTROL Manage Coupon Codes]**&#x200B;选项卡下&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;中的优惠券使用情况。

<u>预期的结果</u>：

如果付款失败，则优惠券不应标记为&#x200B;*已使用*。

<u>实际结果</u>：

* 优惠券代码显示 — 已使用：*是*，使用次数：*1*
* 优惠券代码仅供一次性使用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 安装修补程序后所需的其他步骤

（本节为可选内容；在应用修补程序后，可能需要执行一些步骤来修复此问题。） 

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
