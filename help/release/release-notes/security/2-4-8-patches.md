---
title: Adobe Commerce 2.4.8安全补丁发行说明
description: 了解Adobe Commerce版本2.4.7的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: b0756431d8ddf0833ef8c13528f7681a1a92a3ca
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# Adobe Commerce 2.4.8安全修补程序的发行说明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p3

Adobe Commerce 2.4.8-p3安全版本为2.4.8早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-94](https://helpx.adobe.com/cn/security/products/magento/apsb25-94.html)。

{{b2b-patches}}

### 高亮

此版本包括以下功能亮点：

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* 对ACP2E-3874的修复：现在，订购了多个相同项目时，订单详细信息的REST API响应将包含`base_row_total`和`row_total`属性的正确值。

* 修复了 — AC-15446：修复了`Magento\Framework\Mail\EmailMessage`中的一个错误，其中`getBodyText()`尝试在`getTextBody()`上调用不存在的`Symfony\Component\Mime\Message`方法，从而确保与Magento 2.4.8-p2和`magento/framework` 103.0.8-p2的兼容性。

{{oct-2025-backports}}<!--AC-15446-->

## 2.4.8-p2

Adobe Commerce 2.4.8-p2安全版本为2.4.8早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-71](https://helpx.adobe.com/cn/security/products/magento/apsb25-71.html)。

{{b2b-patches}}

## 2.4.8-p1

Adobe Commerce 2.4.8-p1安全版本为2.4.8早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-50](https://helpx.adobe.com/cn/security/products/magento/apsb25-50.html)。

{{b2b-patches}}

### 高亮

此版本包括以下功能亮点：

* **API性能增强** — 解决在上一个安全修补程序之后引入的批量异步Web API端点中的性能降级。<!-- AC-14078 -->

* **CMS阻止访问修复** — 解决具有受限权限（例如仅限促销访问）的管理员用户无法查看[!UICONTROL CMS Blocks]列表页的问题。

  以前，这些用户在安装以前的安全修补程序后由于缺少配置参数而遇到错误。<!-- AC-14087 -->

* **Cookie限制兼容性** — 解决涉及框架中`MAX_NUM_COOKIES`常量的向后不兼容的更改。 此更新将恢复预期行为，并确保与Cookie限制交互的扩展或自定义设置的兼容性。<!-- AC-14475 -->

* **异步操作** — 用于覆盖先前客户订单的异步操作受限。<!-- AC-13917 -->

* **修复了CVE-2025-47110** — 解决了电子邮件模板漏洞。<!-- AC-14695 -->

* **修复VULN-31547** — 解决类别规范链接漏洞。<!-- AC-14713 -->

>[!BEGINSHADEBOX]

CVE-2025-47110和VULN-31547的修补程序也作为独立修补程序提供。 有关详细信息，请参阅[知识库文章](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)。

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2025-10-06 13:12:34 -->
