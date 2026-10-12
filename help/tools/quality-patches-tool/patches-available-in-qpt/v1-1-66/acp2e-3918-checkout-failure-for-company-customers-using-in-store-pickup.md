---
title: ACP2E-3918：使用店内取货的公司客户签出失败
description: 应用ACP2E-3918修补程序以修复Adobe Commerce问题，该问题导致在没有默认账单地址的情况下使用店内提货的登录公司客户无法结账。
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '384'
ht-degree: 0%
---
# ACP2E-3918：使用店内取货的公司客户签出失败

ACP2E-3918修补程序修复了以下问题：使用无默认账单地址的店内提货的登录公司客户无法结账。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66时，此修补程序可用。 修补程序ID为ACP2E-3918。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当没有默认地址的登录公司客户尝试使用店内取货下达采购订单时，签出失败。

<u>重现步骤</u>：

1. 启用&#x200B;**[!UICONTROL Purchase Orders]**。
1. 创建一个&#x200B;**[!UICONTROL Company]**&#x200B;并为其启用&#x200B;**[!UICONTROL Purchase Orders]**。
1. 创建不带已保存地址的&#x200B;**[!UICONTROL Company User]**。
1. 启用&#x200B;**[!UICONTROL In-Store Delivery]**&#x200B;配送方式。
1. 添加库存来源。
1. 添加库存库存。
1. 将库存分配给产品。
1. 前端，以公司用户身份登录。
1. 将产品添加到&#x200B;**[!UICONTROL Cart]**。
1. 继续结帐。
1. 在配送步骤中选择&#x200B;**[!UICONTROL In-Store Pick Up]**。
1. 继续付款。

<u>预期的结果</u>：

结账期间付款步骤应成功加载，且浏览器控制台中应不会显示任何错误。

<u>实际结果</u>：

支付步骤未加载，且浏览器控制台显示以下JavaScript错误：

```text
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
