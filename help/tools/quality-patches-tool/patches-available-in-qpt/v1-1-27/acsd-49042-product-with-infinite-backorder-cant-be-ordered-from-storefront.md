---
title: ACSD-49042：无法从店面订购具有无限延交订单的产品
description: 应用ACSD-49042补丁以修复无法从店面订购无限延交产品的Adobe Commerce问题。
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
exl-id: b94d06c0-806a-40be-bcd4-d6b8e5e474c3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49042：无法从店面订购具有无限延交订单的产品

ACSD-49042修补程序修复了无法从店面订购具有无限延交订单的产品的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27时，此修补程序可用。 修补程序ID为ACSD-49042。 请注意，Adobe Commerce 2.4.5中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当无法从店面订购具有无限延交订单的产品时，会发生此错误。

<u>重现步骤</u>：

1. 设置以下配置设置：
   * **[!UICONTROL Display Out of Stock Products]**&#x200B;设置为&#x200B;*[!UICONTROL Yes]*。
   * **[!UICONTROL Backorders]**&#x200B;设置为&#x200B;*[!UICONTROL Allow Qty Below 0]*。
1. 添加新的&#x200B;**[!DNL custom stock]**&#x200B;和&#x200B;**[!DNL custom source]**。
1. 将产品分配给&#x200B;**[!DNL custom source]**&#x200B;并确保为其设置了库存编号（例如： *10*）。
1. 在产品编辑页面上，打开&#x200B;**[!UICONTROL Advanced Inventory]**。 在购物车中设置&#x200B;**[!UICONTROL minimum quantity]**（例如： *160*）。 数量必须高于库存。
1. 前往店面购买产品以创建预订。
1. 将&#x200B;**[!UICONTROL product quantity]**&#x200B;更改为&#x200B;*0*。 关键点是在存在预订时从&#x200B;**[!DNL Admin panel]**&#x200B;中保存产品。
1. 打开店面上的&#x200B;**[!UICONTROL product page]**，尝试将产品添加到购物车。

<u>预期的结果</u>：

可以将产品添加到购物车，因为允许对低于&#x200B;*0*&#x200B;的数量延期交货。

<u>实际结果</u>：

产品显示为缺货。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
