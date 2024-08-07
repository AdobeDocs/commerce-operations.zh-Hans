---
title: 内容安全策略概述
description: 了解如何使用内容安全策略改进Adobe Commerce存储的安全状态。
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# 内容安全策略概述

内容安全策略(CSP)可以帮助检测和缓解跨站点脚本(XSS)攻击和相关数据注入攻击，从而为Adobe Commerce安装提供额外的防御层。 这种常见的攻击向量通过注入恶意内容来工作，这些内容错误地声称来自网站。 当恶意内容被加载并执行后，就会启动未经授权的数据传输。

CSP提供了一组标准化的指令，用于告知浏览器哪些内容资源可信，哪些内容应被阻止。 使用仔细定义的策略，CSP可以限制浏览器内容，以仅允许显示已列入白名单的资源。

## 配置

为避免干扰站点操作，可分阶段实施CSP。 CSP有两种基本操作模式： `report-only mode`和`restrict mode`。

**仅报告模式**：指示浏览器报告策略违规，但不强制执行这些违规。 每次请求的资源违反CSP时，浏览器都会将生成的错误记录到控制台。 然后，可以使用控制台日志调查每个违规的原因。

务必在所有CSP错误发生时审查这些错误，并优化策略，直到所有必要的资源都列入白名单为止。 当不再发生错误时，可以安全地切换到`restrict mode`。 否则，配置不佳的CSP可能会导致浏览器显示包含大量控制台错误的空白页面。 通过正确配置的CSP，可以投放已列入白名单的内容，而不会对性能造成任何明显影响。

**限制模式**：指示浏览器强制实施所有内容策略并将发布限制到已列入白名单的资源。

Adobe Commerce CSP实施的第一阶段引入了Adobe Commerce 2.3.5中，并默认在`report-only mode`中提供CSP。  在Adobe Commerce 2.4.7及更高版本中，对于店面和管理区域中的付款页面，CSP默认配置为`restrict-mode`，对于所有其他页面，则配置为`report-only`模式。 相应的CSP标头在付款页的`script-src`指令中不包含关键字`unsafe-inline`。 此外，只允许使用已列入白名单的内联脚本。

由于CSP是从服务器（而不是管理员）配置的，因此大多数商家需要系统集成商或开发人员的帮助才能正确配置它。 请参阅&#x200B;_Commerce PHP开发人员指南_&#x200B;中的[内容安全策略](https://developer.adobe.com/commerce/php/development/security/content-security-policies/)。


## 报表

默认情况下，CSP会向浏览器控制台发送错误，但可以配置为通过HTTP请求收集错误日志。 此外，您还可以使用多种第三方服务来监控、收集和报告CSP违规。 通过从管理员或自定义模块的`config.xml`文件中添加URI，可以将CSP违规报告给端点，以进行收集。  请参阅&#x200B;_Commerce PHP扩展开发人员指南_&#x200B;中的[报告URI配置](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration)。

[报告URI](https://report-uri.io/)是一项监视CSP违规并在仪表板中显示结果的服务。 商家和开发人员都可以使用此服务在CSP违规发生时接收报告。
