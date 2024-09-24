---
title: 'ACSD-54966：修复了在订单失败后重用优惠券代码的问题'
description: 应用ACSD-54966补丁以修复Adobe Commerce问题，防止重复使用以前失败的订单中每个促销和购物车限制的优惠券代码。
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-54966：修复了在订单失败后重用优惠券代码的问题

ACSD-54966修补程序修复了以下问题：在先前失败的订单之后，无法重新使用每个客户限定的优惠券代码。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42时，此修补程序可用。 修补程序ID为ACSD-54966。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在上次订购失败后，不能重复使用仅限于每位客户单次使用的优惠券代码。

<u>重现步骤</u>：

1. 使用&#x200B;*[!UICONTROL Uses per Customer]* = *1*&#x200B;设置购物车价格规则。
1. 继续使用分配的优惠券代码进行购买。
1. 从管理员面板取消订单，或在付款失败时执行订单。
1. 运行命令： `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. 尝试使用同一客户的相同优惠券代码下后续订单。

<u>预期的结果</u>：

在取消订单或遇到付款失败后，客户可以成功地重新使用优惠券代码进行新购买。

<u>实际结果</u>：

客户无法重用优惠券代码。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
