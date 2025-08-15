---
title: ACP2E-3918：使用店内取货的公司客户签出失败
description: 应用ACP2E-3918修补程序以修复Adobe Commerce问题，该问题导致在没有默认账单地址的情况下使用店内提货的登录公司客户无法结账。
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
source-git-commit: fcbc85eaa6aceb5c02929d5b9dbee24f184c03b4
workflow-type: tm+mt
source-wordcount: '359'
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
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

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

```
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
