---
title: ACSD-53643：下达采购订单时，订单总计不正确
description: 应用ACSD-53643修补程序以修复以下问题：订购禁用或缺货的产品时，Adobe Commerce订单总额不正确。
feature: B2B
role: Admin, Developer
exl-id: 72b52695-ef3c-4143-9e77-901463d4a9ed
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-53643：下达采购订单时，订单总计不正确

ACSD-53643修补程序修复了在订购禁用或缺货产品的采购订单时，订单总额不正确的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41时，此修补程序可用。 修补程序ID为ACSD-53643。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订购禁用或缺货的产品时，订单总计不正确。

<u>重现步骤</u>：

1. 安装&#x200B;*[!UICONTROL B2B]*&#x200B;和&#x200B;*[!UICONTROL Inventory]*。
1. 前往&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]**&#x200B;并将&#x200B;**[!UICONTROL Company]** = *是*&#x200B;和&#x200B;**[!UICONTROL Purchase Order]** = *是*。
1. 清除配置缓存。
1. 创建一个新公司，激活它，并为该公司启用&#x200B;*[!UICONTROL Purchase order]*。
1. 为公司创建新用户。
1. 创建&#x200B;*审批规则*&#x200B;以审批公司管理员超过&#x200B;*1 USD*&#x200B;的所有订单。
1. 创建其他源。
1. 以新公司用户的身份登录。
1. 将两个产品添加到购物车并下达采购订单。
1. 禁用第二个产品。
1. 以公司管理员身份登录。
1. 打开采购订单，然后查看该采购订单是否同时包含产品，并且合计是两个产品的合计。
1. 审批采购订单。
1. 下订单。
1. 打开订单详细信息。

<u>预期的结果</u>：

* 即使订单中有一个产品是&#x200B;*已禁用*&#x200B;或&#x200B;*缺货*，也无法下订单。
* *[!UICONTROL Place Order]*&#x200B;按钮已隐藏。

<u>实际结果</u>：

所下的订单仅包含第一个有效产品，但会计算两个产品的订单合计。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
