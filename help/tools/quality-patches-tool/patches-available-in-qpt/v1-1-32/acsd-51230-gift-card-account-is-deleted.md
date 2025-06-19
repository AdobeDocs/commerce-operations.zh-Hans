---
title: ACSD-51230：已删除礼品卡帐户
description: 应用ACSD-51230修补程序以修复以下问题：当订单中的简单产品部分退款被处理时，Adobe Commerce帐户会被删除。
feature: Customer Service, Gift, Marketing Tools
role: Admin
exl-id: a4aed574-3908-42e0-ac32-911f61b44995
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-51230：已删除礼品卡帐户

ACSD-51230修补程序修复了在订单中处理简单产品的部分退款时删除礼品卡帐户的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.32时，此修补程序可用。 修补程序ID为ACSD-51230。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当从订单中处理简单产品的部分退款时，删除礼品卡帐户。

<u>重现步骤</u>：

1. 使用&#x200B;*礼品卡*&#x200B;和&#x200B;*简单产品*&#x200B;创建订单(例如，*add： SKU： GI000XX000XXX， SKU： PC046CP042076*) - （任何付款和送货方式都有效）。
1. 为订单开票。
1. 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**。 为礼品卡创建帐户。
1. 现在转到&#x200B;**[!UICONTROL Order]**&#x200B;并创建&#x200B;**[!UICONTROL Credit Memo]**。
1. 将&#x200B;*礼品卡*&#x200B;的数量更改为0并更新。 这将为&#x200B;*简单产品*&#x200B;创建部分退款。
1. 单击&#x200B;**[!UICONTROL Refund]**。
1. 现在刷新&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**。 新创建的帐户将被删除。

<u>预期的结果</u>

礼品卡帐户可供使用，因为未为礼品卡创建退款。

<u>实际结果</u>

删除礼品卡帐户，且礼品卡不退款。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
