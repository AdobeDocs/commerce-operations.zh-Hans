---
title: ACSD-47875：无法通过库存管理将产品添加到购物车以商店查看范围
description: 应用ACSD-47875修补程序以修复Adobe Commerce问题，该问题导致无法通过清单管理将产品从管理员添加到特定商店视图范围的客户购物车中。
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: 10862e09-d561-4ed5-ab6f-cf002fae6850
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ACSD-47875：无法通过库存管理将产品添加到购物车以商店查看范围

ACSD-47875修补程序修复了以下问题：在具有库存管理的特定商店视图范围内，无法从管理员将产品添加到客户购物车中。 安装[!DNL Quality Patches Tool (QPT)] 1.1.36时，此修补程序可用。 修补程序ID为ACSD-47875。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于安装了MSI的特定商店视图范围，管理员用户无法使用管理员中的&#x200B;**[!UICONTROL Manage Shopping Cart]**&#x200B;功能将产品添加到客户购物车。

<u>先决条件</u>：

[!DNL Adobe Commerce Inventory Management (MSI)]模块已安装并启用。

<u>重现步骤</u>：

1. 创建网站、商店和商店视图。
1. 创建除&#x200B;*默认*&#x200B;之外的其他源。
1. 创建一个新库存，并将其分配给新网站和新来源。
1. 为新网站创建新客户。
1. 仅将产品分配给新网站；从默认网站中取消分配。

   * 分配新源，并将新源的Qty *设置为0*&#x200B;以上，将默认源的&#x200B;*0*&#x200B;设置为。

1. 转到Admin中的&#x200B;**[!UICONTROL Customer Edit]**&#x200B;页面。 单击&#x200B;**[!UICONTROL Manage Shopping Cart]**。
1. 将存储视图范围更改为新的存储视图。
1. 转到&#x200B;**[!UICONTROL Products]**&#x200B;部分并搜索产品。
1. 选择产品并单击&#x200B;**[!UICONTROL Add selections to my cart]**。

<u>预期的结果</u>：

产品即添加到购物车。

<u>实际结果</u>：

* 引发以下错误：*您尝试添加的产品不可用。*
* 产品未添加到购物车。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
