---
title: 自托管概述
description: 了解要考虑的自托管最佳实践。 主题范围从安全元素到灾难恢复等等。 这些主题旨在帮助决定托管自身Adobe Commerce版本的公司。 所展示的项目并非全包罗万象，但应提供一系列良好的概念，以推动建立一个安全、稳定且可复原的网站。
landing-page-description: 了解自行托管Adobe Commerce时要考虑的一些概念和事项。
short-description: 了解自行托管Adobe Commerce的策略和概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 1c63d082-c6fb-4795-81cd-75d097c03e6b
feature: Install
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# 自托管Adobe Commerce概述

在考虑转向Adobe Commerce等电子商务平台时，你可以有充分的选择。 然而，由于该等选择权，须考虑额外成本、风险及负债。 托管Commerce站点可以使用打包解决方案完成，例如[云基础架构上的Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}，其中基础架构、服务器、电子邮件、SSL证书等已预配置并可供使用。 在云基础架构上寻找Adobe Commerce等良好的托管解决方案可简化整个过程，因此有令人信服的原因需要自行托管Commerce站点。 在随附的页面中，有许多主题提供了有关自托管提供的服务、技术和概念的洞察和指导。 此处的信息并非详尽无遗，也不建议您实施所有建议。 但是，这些文章可以帮助您了解使Adobe Commerce自托管尽可能稳定和安全的一些想法和概念。

如果您不使用云基础架构上的Adobe Commerce，则使用的术语包括自托管或内部部署，甚至包括内部部署。 内部部署不仅意味着在一个公司拥有的大楼内的数据中心中。 此术语代表Adobe Commerce未在其基础架构上管理支持的任何内容。 有些托管公司是面向Adobe Commerce的，它们也被视为自托管或内部部署。

关于Adobe Commerce和Magento开放源代码，提供的大多数建议和提示适用于任一版本。 尽管它可能不会直接说明这一点，但人们期望它适用于这两者。 在有关Adobe Commerce的自托管选项的主题中，将同时考虑两个版本。 最后，选择大多数与[云基础架构上的Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}相关的主题作为托管提供程序。

## 术语级别集

以下术语在Experience League文章中经常使用，在与DevOps团队交谈以及与Company Support合作时：

* **DevOps**&#x200B;是一个术语，用于描述处理服务器设置、配置、管理、SSL证书以及有关用于运行Adobe Commerce站点的实际服务器和服务的所有其他内容的团队。 此术语用于帮助指定开发人员的责任通常何时结束，以及基础架构团队的分级和支持从何处开始。

* **安全概念**&#x200B;包含了几个主题和考虑事项，以使Adobe Commerce代码库、文件和文件系统位于服务器上，以及减少许多已知利用漏洞模式的攻击面的任何配置或更新。

* **监控工具**&#x200B;涵盖了一些监控Adobe Commerce网站的现有工具和服务。 这些工具有时提供有关如何改进项目的提示，或发现问题和安全漏洞。

* **灾难恢复**&#x200B;有助于为损坏或利用漏洞项目的不幸事件提供一些概念和注意事项。

* **性能提示**&#x200B;提供了一些使Adobe Commerce应用程序尽可能提高性能的专业提示和指导。

* **错误操作者**&#x200B;是用于尝试执行恶意或未经授权的操作的人员或团队的术语。 它不仅适用于商业应用程序，还可以扩展到与网站相关的基础架构或任何组件。

* **Web应用程序防火墙** (WAF)可通过监视每个指向商业应用程序的请求标题来提供帮助，并阻止已知模式和攻击。 通常，WAF与自定义筛选器和规则结合使用，以帮助管理DDOS攻击。

* **分布式拒绝服务** (DDoS)是一种攻击方法，强制运行网站的服务器使用具有足够数量的虚假请求来使用，使其无法再响应合法请求。

## 接下来呢？

这些主题没有任何特殊顺序或顺序。 它们旨在为DevOps工程师、Commerce架构师以及参与做出此重要决策(决定如何托管Adobe Commerce)的任何其他人员提供要点。

{{$include /help/_includes/hosting-related-links.md}}
