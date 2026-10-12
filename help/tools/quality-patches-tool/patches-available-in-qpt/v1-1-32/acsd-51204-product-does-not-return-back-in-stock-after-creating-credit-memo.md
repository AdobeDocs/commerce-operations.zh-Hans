---
title: ACSD-51204：创建贷项通知单后，产品未返回库存
description: 应用ACSD-51204补丁以修复Adobe Commerce问题，该问题导致产品在创建贷项通知单后未重新补充库存。
feature: Orders, Products, Returns
role: Admin
exl-id: a4dba28c-c239-4812-8b3a-ce0493f9b1aa
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%
---
# ACSD-51204：创建贷项通知单后，产品未返回库存

ACSD-51204修补程序修复了在创建贷项通知单后产品未重新上架的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32时，此修补程序可用。 修补程序ID为ACSD-51204。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

已售出的产品在创建贷项通知单后未返回库存。

<u>重现步骤</u>：

1. 安装&#x200B;**[!UICONTROL Adobe Commerce]**&#x200B;并仅使用默认的&#x200B;*源*&#x200B;和&#x200B;*stock*&#x200B;启用&#x200B;**[!UICONTROL Inventory Management Module]**。
1. 添加数量为&#x200B;*10*&#x200B;的&#x200B;**[!UICONTROL new product]**。
1. 将产品分配给&#x200B;**[!UICONTROL default stock]**。
1. 在店面，将产品添加到购物车中，并下达整个可用数量10的订单。
1. 在管理面板中，为订单生成&#x200B;*发票*&#x200B;和&#x200B;*装运*。
1. 创建针对所有项目选中了&#x200B;*返回库存*&#x200B;复选框的&#x200B;**[!UICONTROL Credit Memo]**。
1. 在管理员中检查产品的&#x200B;**[!UICONTROL Salable Quantity]**。

<u>预期的结果</u>：

产品的可销售数量必须返回到&#x200B;*10*。

<u>实际结果</u>：

产品的可销售数量保留为&#x200B;*0*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
