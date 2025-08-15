---
title: ACSD-51735：当产品库存为0时，订单项目状态错误地设置为*[!UICONTROL Ordered]*
description: 应用ACSD-51735修补程序以修复当产品库存为0时，订单项状态错误设置为*[!UICONTROL Ordered]*的Adobe Commerce问题。
feature: Orders, Products
role: Admin
exl-id: 56c8b58c-819f-46bd-8912-f543f56b66d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-51735：当产品库存为0时，订单项目状态错误地设置为&#x200B;*[!UICONTROL Ordered]*

ACSD-51735修补程序修复了当产品库存为0时，订单项状态错误设置为&#x200B;*[!UICONTROL Ordered]*&#x200B;的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33时，此修补程序可用。 修补程序ID为ACSD-50895。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当产品库存为0时，订单项目状态错误地设置为&#x200B;*[!UICONTROL Ordered]*。

<u>先决条件</u>：

* Adobe Commerce Inventory management (MSI)模块已安装。
* 已在&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**&#x200B;中启用延交。

<u>重现步骤</u>：

1. 创建新库存。
1. 创建新源。
1. 将默认网站分配给新库存，并分配新来源。
1. 创建新产品。

   * 将默认来源数量设置为10，将新来源数量设置为0。

1. 将产品添加到店面的购物车中。
1. 观察结账时的延期交货警告，表明产品来自新来源。
1. 下订单。
1. 在“管理员”中打开订单，然后检查延交订单状态。

<u>预期的结果</u>：

顺序显示Qty 1已延交。

<u>实际结果</u>：

顺序显示数量1是已订购的，而不是已延交。

>[!MORELIKETHIS]
>
>[订单项目状态错误设置为&#x200B;*[!UICONTROL Backordered]*](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
