---
title: ACSD-62118：对于使用[!UICONTROL Purchase Order]方法下达的B2B订单，“sales_order_tax_item”表未完全更新
description: 应用ACSD-62118修补程序以修复使用[!UICONTROL Purchase Order]方法下达B2B订单时，“sales_order_tax_item”表未完全更新的Adobe Commerce问题。
feature: Purchase Orders, B2B
role: Admin, Developer
exl-id: 8ace73ad-f5a5-47ab-aca7-62c818775d2f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%
---
# ACSD-62118：对于使用[!UICONTROL Purchase Order]方法下达的B2B订单，`sales_order_tax_item`表未完全更新

ACSD-62118修补程序修复了使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;方法下达B2B订单时，`sales_order_tax_item`表未完全更新的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-62118。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;方法下达B2B订单时，`sales_order_tax_item`表未完全更新。 此问题会影响税收计算和订单处理。 具体而言，通过API查询订单时，`applied_taxes`数组为空，`tax_item_amount`和`tax_item_percent`均为NULL。

<u>重现步骤</u>：

1. 为&#x200B;**[!UICONTROL Product]**&#x200B;和&#x200B;**[!UICONTROL Shipping]**&#x200B;添加税则。
1. 在公司设置中启用&#x200B;**[!UICONTROL Purchase Order]**&#x200B;方法。
1. 以公司管理员用户身份登录。
1. 使用离线付款方式放置&#x200B;**[!UICONTROL Purchase Order]**。
1. 自动批准[!UICONTROL Purchase Order]并转换为订单后，在`sales_order_tax_item`表中并通过REST API检查税务数据。

<u>预期的结果</u>：

* `sales_order_tax_item`表应包含`tax_item`数据。
* `applied_taxes`数组应在采购订单的API响应中显示正确的税务信息，类似于其他付款方法（例如，支票/货币订单）。

<u>实际结果</u>：

* `sales_order_tax_item`表不包含任何`tax_item`数据。
* *[!UICONTROL Purchase Order]*&#x200B;的API响应中的`applied_taxes`和`item_applied_taxes`数组为空。
* 使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;付款方式时未显示税务数据。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
