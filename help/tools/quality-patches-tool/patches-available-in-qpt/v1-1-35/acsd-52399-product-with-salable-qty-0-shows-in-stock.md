---
title: ACSD-52399：可销售数量0的产品有库存
description: 应用ACSD-52399修补程序以修复Adobe Commerce问题，该问题导致可销售数量为0的可配置产品选项在产品页面上显示*In Stock*。
feature: Products, Configuration
role: Admin, Developer
exl-id: 7b7332bb-15ae-44b6-a347-38ac7c9001db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-52399：可销售数量0的产品有库存

ACSD-52399修补程序修复了可销售数量为零(0)的可配置产品选项在产品页面上显示&#x200B;*In Stock*&#x200B;的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.35时，此修补程序可用。 修补程序ID为ACSD-52399。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

可销售数量为零(0)的可配置产品选项在产品页面上显示&#x200B;*库存*。

<u>重现步骤</u>：

1. 使用零(0)可销售数量产品选项创建可配置产品。
1. 转到店面上的产品页面，然后选择可配置的产品以检查变体/配置。
1. 选择&#x200B;**[!UICONTROL Add to Cart]**。

<u>预期的结果</u>：

选择&#x200B;*[!UICONTROL Add to Cart]*&#x200B;缺货&#x200B;*产品配置时，*&#x200B;按钮不可用。

<u>实际结果</u>：

可配置的变体位于店面上，您可以选择它们并将其添加到购物车中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
