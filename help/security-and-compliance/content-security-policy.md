---
title: 内容安全策略概述
description: 了解如何使用内容安全策略来改进Adobe Commerce或Magento Open Source存储的安全态势。
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# 内容安全策略概述

内容安全策略(CSP)可帮助检测和缓解跨站点脚本(XSS)和相关数据注入攻击，从而为Adobe Commerce和Magento Open Source安装提供额外的防御层面。 这种常见的攻击矢量通过注入错误地声称源自网站的恶意内容来工作。 恶意内容加载和执行后，可以启动未授权的数据传输。

CSP提供了一组标准化指令，用于告知浏览器哪些内容资源可信以及哪些内容资源应被阻止。 使用仔细定义的策略，CSP可以限制浏览器内容以仅允许显示列入白名单的资源。

## 配置

为避免干扰站点操作，可以分阶段实施CSP。 CSP有两种基本的操作模式： `report-only mode` 和 `restrict mode`. Adobe Commerce 2.3.5的发布标志着我们实施的第一个阶段，并在 `report-only mode` 默认情况下。 在将来的版本中， `restrict mode` 默认情况下，启用附加的现成保护。

**仅报告模式**:系统会指示浏览器报告策略违规，但不会强制执行。 每次请求的资源违反CSP时，浏览器都会将导致的错误记录到控制台。 然后，可以使用控制台日志来调查每个违规的原因。

务必在发生所有CSP错误时对其进行审核，并优化策略，直到将所有必需资源列入白名单为止。 可以安全地切换到 `restrict mode` 不再发生错误时。 否则，配置不当的CSP可能会导致浏览器显示一个包含大量控制台错误的空白页面。 正确配置的CSP允许交付已列入白名单的内容，而不会对性能产生任何感知影响。

**限制模式**:系统将指示浏览器强制实施所有内容策略，并将发布限制为已列入白名单的资源。 由于CSP是从服务器而不是管理员配置的，因此大多数商家都需要系统集成商或开发人员的帮助才能正确配置CSP。 请参阅 [内容安全策略](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 在 _商务PHP扩展_ 开发人员指南。

## 报表

默认情况下，CSP会向浏览器控制台发送错误，但可以将其配置为通过HTTP请求收集错误日志。 此外，您还可以使用若干第三方服务来监控、收集和报告CSP违规情况。

[报表URI](https://report-uri.io/) 是一项服务，可监视CSP违规情况并在功能板中显示结果。 每当发生CSP违规时，商家和开发人员都可以使用该服务来接收报表。
