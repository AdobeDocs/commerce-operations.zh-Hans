---
title: 'ACSD-46683：配送价格显示*尚未计算*'
description: 应用ACSD-46683修补程序以修复发货价格显示*尚未计算*的Adobe Commerce问题。
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683：配送价格显示&#x200B;*尚未计算*

ACSD-46683修补程序修复了发货价格显示&#x200B;*尚未计算*&#x200B;的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30时，此修补程序可用。 修补程序ID为ACSD-46683。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

运费显示&#x200B;*尚未计算*。

<u>先决条件</u>：

Adobe Commerce Inventory management (MSI)模块已安装。

<u>重现步骤</u>：

1. 创建一个简单的产品并将其价格设置为&#x200B;*$34*。
1. 配置免费送货方式。
1. 配置至少一个以上的投放方法。
1. 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**&#x200B;并创建新规则：
   * 名称= *75more*
   * 优惠券=无
   * 优先级= 1
   * 条件：小计等于或大于&#x200B;*$75*
   * 操作：
      * 应用于发运金额=是
      * 放弃后续规则=否
      * 免费发运=对于具有匹配物料的发运
1. 创建另一个购物车价格规则：
   * 名称= *35off*
   * 优先级= 0
   * 优惠券=特定优惠券
   * 优惠券代码= 35折扣
   * 操作：
      * 应用=产品价格折扣的百分比
      * 折扣金额= 35
      * 应用于装运金额=否
      * 放弃后续规则=是
      * 免费送货=否
1. 打开店面，然后将三个产品添加到购物车，以使小计超过$75。
1. 以来宾身份继续结帐。
1. 在送货步骤中，选择&#x200B;**$0 — 免费送货**，然后继续付款步骤。
1. 检查付款步骤中的[!UICONTROL Order Summary]。 它显示&#x200B;*[!UICONTROL $0 - Free Shipping - Free]*。
1. 应用优惠券代码&#x200B;*35off*，它将更新小计并使其小于$75。
1. 在付款步骤中检查[!UICONTROL Order Summary]。

<u>预期的结果</u>：

显示以下消息： *所选的配送方式不可用。 请选择此订单的其他配送方式。*

<u>实际结果</u>：

配送价格显示&#x200B;*尚未计算*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
