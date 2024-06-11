---
title: Adobe Commerce 2.4.7安全修补程序发行说明
description: 了解Adobe Commerce版本2.4.7的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Adobe Commerce 2.4.7安全修补程序的发行说明

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

Adobe Commerce 2.4.7-p1安全版本修复了2.4.7早期版本中发现的漏洞。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

## 安全性突出显示

此版本包括对 [一次性密码(OTP)设置](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) 用于Google Authenticator，以解决由引入的错误。 [向后不兼容的更改](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) 在2.4.7中。的描述 **[!UICONTROL OTP Window]** 字段现在提供了设置的准确说明，并且默认值已从 `1` 到 `29`.