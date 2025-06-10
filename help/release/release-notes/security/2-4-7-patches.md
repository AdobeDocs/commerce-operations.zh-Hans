---
title: Adobe Commerce 2.4.7安全修补程序发行说明
description: 了解Adobe Commerce版本2.4.7的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 11044555f0e661fcbdbb5e6a41b9790ca244f31a
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Adobe Commerce 2.4.7安全修补程序的发行说明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7 - p6

Adobe Commerce 2.4.7-p6安全版本为2.4.7早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html)。

{{b2b-patches}}

### 高亮

此版本包括以下功能亮点：

* **MariaDB支持** — 添加了对MariaDB 10.11的支持。

* **API性能增强** — 解决在上一个安全修补程序之后引入的批量异步Web API端点中的性能降级。<!-- AC-14078 -->

* **CMS阻止访问修复** — 解决具有受限权限（例如仅限促销访问）的管理员用户无法查看[!UICONTROL CMS Blocks]列表页的问题。

  以前，这些用户在安装以前的安全修补程序后由于缺少配置参数而遇到错误。<!-- AC-14087 -->

* **Cookie限制兼容性** — 解决涉及框架中`MAX_NUM_COOKIES`常量的向后不兼容的更改。 此更新将恢复预期行为，并确保与Cookie限制交互的扩展或自定义设置的兼容性。<!-- AC-14475 -->

* **修复CVE-2024-34104** — 解决不正确的授权漏洞。<!-- AC-13917 -->

* **修复了CVE-2025-47110** — 解决了电子邮件模板漏洞。<!-- AC-14695 -->

>[!BEGINSHADEBOX]

CVE-2025-47110的修补程序也作为独立修补程序提供。 有关详细信息，请参阅[知识库文章](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)。

>[!ENDSHADEBOX]

## 2.4.7 - p5

Adobe Commerce 2.4.7-p5安全版本为2.4.7早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

此版本还引入了对Adobe Commerce [HIPAA就绪扩展](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview)的支持。

>[!ENDSHADEBOX]

### 已知问题

**问题**：在安装PHP 8.2或更高版本的2.4.7-p5时，系统会安装适用于2.4.8及更高版本的`paypal/module-braintree`版本4.7.0。 对于PHP 8.1，使用正确的Braintree版本4.6.1-p5。 此不匹配是由于对中间包中`adobe-commerce/extensions-metapackage: ~2.0`的依赖性松散所致。 这会影响PHP 8.2+部署的兼容性和支持的功能集。<!-- ACPLTSRV-6276) -->

此外，对于版本2.4.7-p3、2.4.7-p4和2.4.7-p5，可以安装Braintree扩展版本4.6.1-p5，而某些用户期望4.6.1-p3或p4，因为之前已经放松了更严格的依赖关系，允许在发布行中进行扩展升级。<!-- AC-14430 -->

**解决方法**：要确保您的PHP版本具有正确的Braintree版本，请运行`composer update`以安装`adobe-commerce/extensions-metapackage:2.0.0`依赖关系要求的相应版本。

## 2.4.7 - p4

Adobe Commerce 2.4.7-p4安全版本为2.4.7早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7 - p3

Adobe Commerce 2.4.7-p3安全版本为2.4.7早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### 此版本中包含的修补程序

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7 - p2

Adobe Commerce 2.4.7-p2安全版本为2.4.7早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)。

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 此版本中包含的修补程序

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7 - p1

Adobe Commerce 2.4.7-p1安全版本修复了2.4.7早期版本中发现的漏洞。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)。

### 应用适用于CVE-2024-34102的修补程序

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### 高亮

此版本包括以下功能亮点：

* **更新Google Authenticator的[一次性密码(OTP)设置](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google)** — 需要此更新才能解决2.4.7中[向后不兼容的更改](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value)导致的错误。**[!UICONTROL OTP Window]**&#x200B;字段的描述现在提供了设置的准确解释，默认值已从`1`更改为`29`。

* **B2B版本兼容性** — 要与Commerce版本2.4.7-p1兼容，具有Adobe Commerce B2B扩展的商家必须升级到[B2B版本1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)。

### 此版本中包含的修补程序

Adobe Commerce 2.4.7-p1解决了从SOAP迁移到REST API的UPS集成过程中引入的问题。 此问题会影响从美国境外发运的客户，并阻止他们使用公制系统/SI测量值（即包装的公斤和厘米）来创建与UPS的发运。 有关详细信息，请参阅[UPS配送方式集成从SOAP迁移到RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api)知识库文章。
