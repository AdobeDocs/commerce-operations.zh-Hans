---
title: ACSD-47232：选中[!UICONTROL Same as Billing Address]时未应用优惠券
description: 应用ACSD-47232修补程序以修复选中[!UICONTROL Same as Billing Address]后未应用优惠券的Adobe Commerce问题。
feature: Orders, Shipping/Delivery
role: Admin
exl-id: d8050f6e-00a9-4aa3-bb8b-1631e0e7a714
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-47232：选中[!UICONTROL Same as Billing Address]时未应用优惠券

ACSD-47232修补程序修复了在选中&#x200B;**[!UICONTROL Same as Billing Address]**&#x200B;时未应用优惠券的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23时，此修补程序可用。 修补程序ID为ACSD-47232。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

选中&#x200B;**[!UICONTROL Same as Billing Address]**&#x200B;时未应用优惠券。

<u>重现步骤</u>：

1. 安装Adobe Commerce。
1. 创建重量= *8*&#x200B;的简单产品。
1. 使用默认帐单和送货地址创建新客户。
1. 创建包含优惠券的购物车价格规则。
   * 在&#x200B;**[!UICONTROL Conditions]**&#x200B;部分中，添加&#x200B;*总权重等于或大于5*
1. 尝试在[!UICONTROL Commerce]管理员中创建新订单。
   * 使用刚刚创建的客户
   * 添加产品
   * 尝试应用优惠券

<u>预期的结果</u>：

已应用优惠券。

<u>实际结果</u>：

您收到类似于以下内容的错误： *123优惠券代码无效。 请验证代码并重试。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
