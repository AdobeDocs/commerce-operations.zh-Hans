---
title: 云基础架构概述
description: 了解云基础架构上的Adobe Commerce。
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# 概述

AWS上Adobe Commerce最常用的托管选项之一是Adobe Commerce本身。 Adobe Commerce on cloud基础架构是Adobe Commerce软件的一个完全受管的自动托管平台。

云基础架构上的Adobe Commerce是一款平台即服务(PaaS)产品，它允许快速部署完全可自定义、安全且可扩展的Web店面，以及领先的托管和托管服务基础架构。 它提供了两个具有不同基础设施的计划。 Adobe Commerce Starter最适合于复杂度较低、目录较小的较小商店。 Adobe Commerce Pro专为具有更复杂性、更大产品目录或高峰流量的大型商店而构建。 Adobe Commerce将根据合作伙伴的意见确定适当的架构。

Adobe Commerce具备云就绪性和完全冗余的多云托管基础架构，可提供优化的性能、可复原性和弹性可扩展性。 您可以在Fastly的内容分发网络(CDN)上高效地运行您的商务平台，并且借助用于监控和管理的New Relic，您可以保持存储环境的顺畅运行。

Adobe Commerce提供了现代云计算的所有优势，这些优势最常与SaaS解决方案相关联：弹性可扩展性、高可复原性和可用性、 PCI合规性以及全球可用性和自动修补，同时保持我们的商户所需要的软件定制灵活性。

![显示云基础架构上Adobe Commerce的架构元素的图表](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## 优点

Adobe Commerce的其他好处包括：

- **针对Adobe Commerce优化**. Adobe Commerce开发的构建脚本和服务配置可确保正确调整和配置每个实例，以获得最佳的商户性能。

- **一致的安全版本**. 所有代码部署都基于Git，以实现一致性和重复性，并且具有只读生产环境，可增强安全性。

- **合作伙伴的灵活性**. 完整的REST API和可编写脚本的命令行界面可确保轻松与外部系统集成并与现有代码管理工作流兼容。

- **灵活的部署工具集**. 可随意快速启动、合并、克隆和拆除无限制的环境，以用于开发任务、QA测试或生产问题诊断。

- **连续云交付**. 满怀信心地跨代码分支和开发团队，从开发到UAT，直到生产。

## 第三方服务

我们还来看一下让Adobe Commerce的优势成为现实的软件。

![关于云基础架构技术堆栈的Adobe Commerce示意图](../../../assets/playbooks/cloud-tech-stack.svg)

- Fastly CDN:当客户访问您的网站并进行存储时，请求会快速点击以更快地加载缓存的页面。 Fastly WAF还提供DDoS保护服务。

- New Relic为您提供了应用程序和操作环境的完整视图。 它允许您将来自移动设备和浏览器应用程序的关键量度与支持服务、数据存储和主机相结合，从而全面优化性能并确保每项计划的成功。

- 编辑器在Adobe Commerce中管理依赖项和升级，并提供有关包含的包、包的用途以及它们如何组合在一起的上下文。

- Git是存储库中的代码。 它允许本地分支、方便的暂存区域和多个工作流，并可自动构建和部署，以实现高效的快速开发和连续部署。

- 平台即服务(PaaS)提供预配置的基础架构，包括PHP、MySQL、Redis、 [!DNL RabbitMQ]和Elasticsearch技术。

- AWS或Azure的云托管支持基础架构即服务(IaaS)，它为在线销售和零售提供了可扩展且安全的环境。
