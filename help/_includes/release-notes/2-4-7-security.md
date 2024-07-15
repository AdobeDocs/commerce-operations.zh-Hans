---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7安全增强功能

* **添加了Subresource Integrity (SRI)支持**&#x200B;以符合PCI 4.0要求验证支付页面上的脚本完整性。 子资源完整性(SRI)支持为驻留在本地文件系统中的所有JavaScript资源提供完整性哈希。 默认SRI功能仅在管理员和店面区域的支付页面上实施。 但是，商家可以将默认配置扩展到其他页面。 请参阅&#x200B;_Commerce PHP开发人员指南_.<!--AC-1153-->中的[子资源完整性](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/)

* **对内容安全策略(CSP)的更改** — 对Adobe Commerce内容安全策略(CSP)的配置更新和增强以符合PCI 4.0要求。 有关详细信息，请参阅&#x200B;_Commerce PHP Developer Guide_&#x200B;中的[内容安全策略](https://developer.adobe.com/commerce/php/development/security/content-security-policies/)。<!--AC-11513-->

   * Commerce管理员和店面区域的付款页面的默认CSP配置现在为`restrict`模式。 对于所有其他页面，默认配置为`report-only`模式。  在低于2.4.7的版本中，CSP在所有页面中均配置为`report-only`模式。

   * 添加了一个nonce提供程序，以允许在CSP中执行内联脚本。 nonce提供程序有助于为每个请求生成唯一的nonce字符串。 随后，这些字符串将附加到CSP标头。

   * 添加了用于配置自定义URI以报告“管理员”中“创建订单”页面和“店面”中“结帐”页面的CSP违规的选项。 您可以从管理员添加配置，或通过将URI添加到`config.xml`文件来添加。

     >[!NOTE]
     >
     >将CSP配置更新为`restrict`模式可能会阻止管理员和店面中付款页面上现有的内联脚本，这会导致页面加载时出现以下浏览器错误： `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`。 通过更新白名单配置以允许所需的脚本修复这些错误。 请参阅&#x200B;_Commerce PHP开发人员指南_&#x200B;中的[疑难解答](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting)。
