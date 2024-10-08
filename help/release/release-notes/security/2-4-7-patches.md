---
title: Adobe Commerce 2.4.7安全修补程序发行说明
description: 了解Adobe Commerce版本2.4.7的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Adobe Commerce 2.4.7安全修补程序的发行说明

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.7 - p3

Adobe Commerce 2.4.7-p3安全版本为2.4.7早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/2024-10/security-foo.md}}

### 此版本中包含的修补程序

{{$include /help/_includes/release-notes/2024-10/hotfixes-included-foo.md}}

## 2.4.7 - p2

Adobe Commerce 2.4.7-p2安全版本为2.4.7早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)。

### 高亮

{{$include /help/_includes/release-notes/2024-08/security.md}}

### 此版本中包含的修补程序

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.7 - p1

Adobe Commerce 2.4.7-p1安全版本修复了2.4.7早期版本中发现的漏洞。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)。

### 应用适用于CVE-2024-34102的修补程序

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### 高亮

此版本包括以下功能亮点：

* **更新Google Authenticator的[一次性密码(OTP)设置](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google)** — 需要此更新才能解决2.4.7中[向后不兼容的更改](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value)导致的错误。**[!UICONTROL OTP Window]**&#x200B;字段的描述现在提供了设置的准确解释，默认值已从`1`更改为`29`。

* **B2B版本兼容性** — 要与Commerce版本2.4.7-p1兼容，具有Adobe Commerce B2B扩展的商家必须升级到[B2B版本1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)。

### 此版本中包含的修补程序

Adobe Commerce 2.4.7-p1解决了从SOAP迁移到REST API的UPS集成过程中出现的问题。 此问题会影响从美国境外发运的客户，并阻止他们使用公制系统/SI测量值（即包装的公斤和厘米）来创建与UPS的发运。 有关详细信息，请参阅[UPS配送方式集成从SOAP迁移到RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api)知识库文章。
