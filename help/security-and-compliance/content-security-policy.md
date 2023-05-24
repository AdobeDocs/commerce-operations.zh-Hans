---
title: 内容安全策略概述
description: 了解如何使用内容安全策略改进Adobe Commerce或Magento Open Source存储的安全状态。
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# 内容安全策略概述

内容安全策略(CSP)可以帮助检测和缓解跨站点脚本(XSS)攻击和相关数据注入攻击，从而为Adobe Commerce和Magento Open Source安装提供额外的防御层。 这种常见的攻击向量通过注入恶意内容来工作，这些内容错误地声称源自网站。 恶意内容被加载并执行后，可以发起未经授权的数据传输。

CSP提供了一组标准化的指令，用于告知浏览器哪些内容资源可以信任，哪些内容应该被阻止。 使用仔细定义的策略，CSP可以限制浏览器内容，以仅允许显示已列入白名单的资源。

## 配置

为避免干扰站点操作，可以分阶段实施CSP。 CSP有两种基本操作模式： `report-only mode` 和 `restrict mode`. Adobe Commerce 2.3.5的发布标志着我们实施的第一阶段，CSP可用于 `report-only mode` 默认情况下。 在未来版本中， `restrict mode` 默认启用以获得更多开箱即用保护。

**仅报告模式**：指示浏览器报告策略违规，但不强制执行这些违规。 每次请求的资源违反CSP时，浏览器都会将生成的错误记录到控制台。 然后，可以使用控制台日志调查每个违规的原因。

务必要查看所有CSP错误，并优化策略，直到所有必要的资源都列入白名单。 可以安全地切换到 `restrict mode` 不再发生错误时。 否则，配置不佳的CSP可能会导致浏览器显示一个包含大量控制台错误的空白页面。 通过正确配置的CSP，可以交付已列入白名单的内容，而不会对性能造成任何明显影响。

**限制模式**：指示浏览器强制实施所有内容策略，并将发布限制到已列入白名单的资源。 由于CSP是从服务器配置，而不是从管理员配置，因此大多数商家需要系统集成商或开发人员的协助才能正确配置。 参见 [内容安全策略](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 在 _Commerce PHP扩展_ 开发人员指南。

## 报告

默认情况下，CSP会将错误发送到浏览器控制台，但可以配置为通过HTTP请求收集错误日志。 此外，您还可以使用多个第三方服务来监控、收集和报告CSP违规。

[报告URI](https://report-uri.io/) 是一项监视CSP违规并在功能板中显示结果的服务。 商家和开发人员都可以使用此服务在CSP违规发生时接收报告。
