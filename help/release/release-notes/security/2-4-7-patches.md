---
title: Adobe Commerce 2.4.7安全修补程序发行说明
description: 了解Adobe Commerce 2.4.7版安全修补程序版本中包含的安全错误修复、安全增强和其他与安全相关的更新。
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 9bf1c539220d70a8e7fe449e4d91199f23cc23b2
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Adobe Commerce 2.4.7安全修补程序的发行说明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p5

Adobe Commerce 2.4.7-p5安全版本为2.4.7早期版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)。

{{b2b-patches}}

### 高光

此版本引入了对Adobe Commerce [HIPAA就绪扩展](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview)的支持。

## 2.4.7-p4

Adobe Commerce 2.4.7-p4安全版本为2.4.7早期版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)。

{{b2b-patches}}

### 高光

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

Adobe Commerce 2.4.7-p3安全版本为2.4.7早期版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)。

{{b2b-patches}}

### 高光

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### 此版本中包括的修补程序

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

Adobe Commerce 2.4.7-p2安全版本为2.4.7早期版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)。

### 高光

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 此版本中包括的修补程序

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

Adobe Commerce 2.4.7-p1安全版本修复了2.4.7早期版本中发现的漏洞的安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)。

### 应用CVE-2024-34102的修补程序

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### 高光

此版本包括以下亮点：

* **更新Google Authenticator的[一次性密码(OTP)设置](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google)** — 需要此更新才能解决2.4.7中[向后不兼容的更改](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value)造成的错误。**[!UICONTROL OTP Window]**&#x200B;字段的描述现在提供了设置的准确解释，默认值已从`1`更改为`29`。

* **B2B版本兼容性** — 为了与Commerce版本2.4.7-p1兼容，具有Adobe Commerce B2B扩展的商家必须升级到[B2B版本1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)。

### 此版本中包括的修补程序

Adobe Commerce 2.4.7-p1解决了从SOAP到REST API的UPS集成迁移过程中引入的问题。 此问题影响了美国以外地区发运的客户，并阻止他们使用公制系统/SI度量单位（千克与厘米）为包装创建装有UPS的运输。 有关详细信息，请参阅[UPS装运方法集成从SOAP迁移到RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api)知识库文章。
