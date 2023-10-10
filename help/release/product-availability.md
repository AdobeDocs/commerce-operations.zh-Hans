---
title: 产品可用性
description: 了解当前支持哪些Adobe Commerce功能，并检查它们与特定Adobe Commerce版本的兼容性。
exl-id: 7e8e8ac2-a0b9-4023-a813-c0f1293e54c2
source-git-commit: 3592b81b260eee7d3889f3f9cf702d8f13aacae3
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 15%

---

# 产品可用性

下表介绍了Adobe Commerce软件的可用性状态以及获取该可用软件的位置，尤其是对于在常规Adobe Commerce编辑器包之外可用的软件。

在产品发布时，服务和扩展会在最新发布的Commerce版本上进行测试。

Adobe已对支持的版本进行了全面测试。 Adobe客户支持部门可提供受支持版本的帮助。 较旧的版本可能会正常工作，但官方并不支持该版本。

>[!NOTE]
>
>对Adobe Commerce版本的支持还包括对 [可用的安全修补程序](versions.md).

## Adobe创作的扩展

这些Adobe Commerce扩展与核心Adobe Commerce代码库分离。 这允许Adobe在更灵活的时间范围内发布这些扩展的反复版本，并使客户能够更早地访问新功能。


下表显示了每个扩展相对于Adobe Commerce版本的版本支持。

| **Adobe Commerce版本** | 2.4.7-beta2 | 2.4.7-beta1 | 2.4.6 | 2.4.5 | 2.4.4 | 2.4.3 |                                                                                                                                                                                                                                          |
|---------------------------------------|-------------|-------------|--------|--------|--------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _Adobe Commerce的Adobe I/O事件_ | 1.3.0 | 1.3.0 | 1.3.0 | 1.3.0 | 1.3.0 | - | [Composer](https://developer.adobe.com/commerce/extensibility/events/installation/) <br/>[发行说明](https://developer.adobe.com/commerce/extensibility/events/release-notes/) |
| _B2B_ | 1.4.2 | 1.4.0+ | 1.3.5+ | 1.3.4 | 1.3.3 | 1.3.2 | [Composer](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html) <br/> [发行说明](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html) |
| _Experience Platform连接器_ | 3.0.0-beta1 | 3.0.0-beta1 | 1.0.0+ | 1.0.0+ | 1.0.0+ | 1.0.0+ | [市场](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html)<br/>[发行说明](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/release-notes.html) |
| _页面生成器_ | - | - | 1.7.3 | 1.7.2 | 1.7.1 | - | [用户指南](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/guide-overview.html)<br/> [发行说明](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/release-notes.html) |

## Commerce服务

[Commerce服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html) 是一套Adobe托管功能，可与您的Commerce实例一起提供强大的功能和快速的响应时间。

建议商家使用最新版本的服务，以确保最高的稳定性和功能。 本文档介绍了当前发布的版本。

* Adobe Commerce服务当前与Commerce 2.4.4及更高版本兼容。 建议商家使用最新版本的服务。
* 认为服务与以前版本的Commerce 2.4.x兼容，但官方不支持这些服务。
* 服务与Commerce 2.3.x不兼容，但产品Recommendations 3.3.7及更低版本除外。

下表显示了相对于Adobe Commerce版本的每个服务的版本支持。

| **Adobe Commerce版本** | 2.4.7-beta2 | 2.4.7-beta1 | 2.4.6 | 2.4.5 | 2.4.4 | 2.4.3 |                                                                                                                                                                                                                                                |
|----------------------------------------|-------------|-------------|--------|-----------------|-----------------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _AmazonSales Channel_ | - | - | 4.4.0+ | 4.3.0+ | 4.3.0+ | 4.3.0+ | [市场](https://commercemarketplace.adobe.com/magento-module-amazon.html)<br/> [发行说明](https://experienceleague.adobe.com/docs/commerce-channels/amazon/release-notes.html) |
| _Adobe Commerce的目录服务_ | 1.11 | 1.11 | 1.11 | 1.11 | 1.11 | - | [概述](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/guide-overview.html)<br/> [发行说明](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/release-notes.html) |
| _渠道管理器_ | - | - | 2.0.0 | 1.0.0+ | 1.0.0+ | 1.0.0+ | [市场](https://commercemarketplace.adobe.com/magento-channel-manager.html)<br/> [发行说明](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/release-notes.html) |
| _实时搜索_ | 3.0.2 | 3.0.2 | 3.0.2 | 3.0.2 | 3.0.2 | - | [市场](https://commercemarketplace.adobe.com/magento-live-search.html)<br/>[发行说明](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html) |
| _支付服务_ | 2.2.0 | 2.2.0 | 2.2.0 | 2.2.0 (PHP 8.1) | 2.2.0 (PHP 8.1) | - | [市场](https://commercemarketplace.adobe.com/magento-payment-services.html)<br/> [发行说明](https://commercemarketplace.adobe.com/magento-payment-services.html) |
| _产品Recommendations_ | 5.0 | 5.0 | 5.0 | 5.0 | 5.0 | - | [市场](https://commercemarketplace.adobe.com/magento-product-recommendations.html)<br/> [发行说明](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _快速签出_ | - | - | 1.0.0+ | 1.2.0+ | 1.0.0+ | 1.2.0+ | [市场](https://commercemarketplace.adobe.com/magento-quick-checkout.html)<br/> [发行说明](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _Adobe Commerce 的商店履行情况_ | - | - | 1.5.0 | 1.2.0+ | 1.2.0+ | 1.2.0+ | [市场](https://commercemarketplace.adobe.com/store-fulfillment-magento-walmart.html)<br/> [发行说明](https://experienceleague.adobe.com/docs/commerce-merchant-services/store-fulfillment/release-notes.html) |
