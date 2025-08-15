---
source-git-commit: 6ca34e8713f4f138961786de206cd360f0bc1be7
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---
# 2025年2月安全修补程序亮点

此版本包括以下功能亮点：

* **管理加密密钥和重新加密数据** — 重新设计了管理加密密钥以提高可用性并消除以前的限制和错误。<!-- AC-12679 -->

  新CLI命令现在可用于[更改](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/security/encryption-key)密钥和[重新加密](https://developer.adobe.com/commerce/php/development/security/data-encryption/)某些系统配置、付款和自定义字段数据。 此版本不再支持更改管理员UI中的键。 必须使用CLI命令。

* **修复[CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)** — 解决授权漏洞。

  此修复还作为独立修补程序提供。 有关详细信息，请参阅[知识库文章](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08)。<!-- AC-12755 -->

* **TinyMCE版本降级** — 为了解决许可兼容性问题，TinyMCE依赖项已从版本7降级6.8.5。

  在Adobe评估替代开源WYSIWYG编辑器时，此更改可确保持续的合规性。
