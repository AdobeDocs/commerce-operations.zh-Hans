---
title: 自托管概述
description: 了解要考虑的自托管最佳实践。 主题从安全元素到灾难恢复等。 以下主题旨在帮助决定托管其自己版本的Adobe Commerce的公司。 所介绍的项目并非全部包容，但应提供一系列良好的概念，以促进安全、稳定和可复原的网站。
landing-page-description: 了解在您自己托管Adobe Commerce时应考虑的一些概念和事项。
short-description: 了解自行托管Adobe Commerce的策略和概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: ef89ace2f03d5010384ba759e81695b6ae7e630b
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---


# 自托管Adobe Commerce概述

考虑转向Adobe Commerce等电子商务平台时，您可以选择各种选择。 但是，有了这些选项，就会产生额外的成本、风险和负债。 可以使用打包的解决方案(例如 [Adobe Commerce云基础架构](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}，其中预配置了基础结构、服务器、电子邮件、SSL证书等，并可供使用。 在云基础架构上找到诸如Adobe Commerce之类的良好托管解决方案可以简化整个流程，因此自托管您的商务网站的理由非常充分。 在随附的页面中，有许多主题提供了有关自托管所提供的服务、技术和概念的洞察和指导。 此处的信息并不详尽，您不应该实施每个建议。 但是，这些文章可以帮助您了解可以使Adobe Commerce自托管尽可能稳定和安全的想法和概念。

如果您不打算在云基础架构上使用Adobe Commerce，则使用的术语为自托管或内部部署，甚至使用内部部署。 内部部署不仅意味着公司拥有的建筑物中的数据中心。 此术语表示Adobe Commerce未对其基础架构提供管理支持的任何内容。 有些托管公司是为Adobe Commerce服务的，它们也被视为自托管或内部托管。

关于Adobe Commerce和Magento开源，提供的大多数建议和提示适用于任一版本。 尽管它可能不会直接声明，但人们的期望是，它适用于这两种情况。 在此主题中，Adobe Commerce的自托管选项考虑了两个版本。 最后，大多数话题都与 [Adobe Commerce云基础架构](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} 已选择作为托管提供程序。

## 术语级别设置

在与DevOps团队交谈并与公司支持合作时，以下术语通常会在Experience League文章中使用：

* **DevOps** 是一个术语，用于描述负责处理服务器设置、配置、管理、SSL证书以及与用于运行Adobe Commerce站点的实际服务器和服务有关的所有其他服务的团队。 此术语用于帮助指定开发人员的责任通常何时结束以及基础结构团队的测试和支持从何时开始。

* **安全概念** 包括在服务器上制作Adobe Commerce代码库、文件和文件系统以及减少许多已知利用漏洞模式攻击面的任何配置或更新的几个主题和注意事项。

* **监控工具** 包含一些监控Adobe Commerce网站的现有工具和服务。 这些工具有时可以提供有关如何改进工作、发现问题和安全漏洞的提示。

* **灾难恢复** 有助于为受损或被利用项目的不幸事件提供一些概念和注意事项。

* **性能提示** 为尽可能提高Adobe Commerce应用程序的性能提供一些专业提示和指导。

* **坏演员** 是试图执行恶意或未授权操作的人员或团队使用的术语。 它不仅限于商务应用程序，还延伸到基础结构或与网站相关的任何组件。

* **Web应用程序防火墙** (WAF)通过观看商务应用程序的每个请求标题并阻止已知模式和漏洞利用来提供帮助。 通常，WAF会与自定义过滤器和规则结合使用，以帮助管理DDOS攻击。

* **分布式拒绝服务** (DDoS)是一种攻击方法，用于强制运行网站的服务器使用具有足够数量的假请求，以便它们不再能够响应合法请求。

## 接下来是什么？

这些主题没有任何特殊顺序或顺序。 它们旨在为DevOps工程师、商务架构师以及参与决定在何处以及如何托管Adobe Commerce这一重要决策的其他人员提供谈话要点。

{{$include /help/_includes/hosting-related-links.md}}
