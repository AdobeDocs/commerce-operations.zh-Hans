---
title: 云基础架构概述
description: 了解Adobe Commerce on cloud基础架构。
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# 概述

Adobe Commerce本身为AWS上的Adobe Commerce提供了最流行的托管选项之一。 云基础架构上的Adobe Commerce是适用于Adobe Commerce软件的完全托管的自动托管平台。

云基础架构上的Adobe Commerce是一款平台即服务(PaaS)产品，支持快速部署完全可自定义、安全和可扩展的Web存储场，以及领先的托管和Managed Services基础架构。 它提供了两种具有不同基础架构的计划。 Adobe Commerce [简易版](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#starter-projects)计划最适合具有较低复杂性和较小目录的较小商店。 Adobe Commerce [Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#pro-projects)计划适用于具有较高复杂性的大型商店、较大的产品目录或峰值流量。 Adobe通过合作伙伴的输入来确定适当的架构。

Adobe Commerce为云做好准备，具有完全冗余的多云托管基础设施，可提供优化的性能、弹性和弹性可扩展性。 您可以在Fastly的内容交付网络(CDN)上高效地运行您的Commerce平台，并利用New Relic进行监控和管理，您可以保持您的商店环境顺畅运行。

Adobe Commerce提供现代云计算的所有优势，这些优势通常与SaaS解决方案相关联，同时仍保持软件自定义的灵活性：

- 弹性可扩展性
- 高可复原性和可用性
- PCI合规性
- 全局可用性和自动修补

![在云基础架构上显示Adobe Commerce的架构元素的图表](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## 优点

Adobe Commerce的其他优势包括：

- **已为Adobe Commerce优化**。 Adobe Commerce开发的构建脚本和服务配置可确保正确调整和配置每个实例，以获得最佳商家性能。

- **一致、安全的版本**。 所有代码部署都基于Git以实现一致性和可重复性，并带有只读生产环境以实现增强的安全性。

- **合作伙伴的灵活性**。 完整的REST API和可编写脚本的命令行界面可确保与外部系统轻松集成以及与现有代码管理工作流的兼容性。

- **灵活的部署工具集**。 可随意快速启动、合并、克隆和拆除无限数量的环境，执行开发任务、QA测试或生产问题诊断。

- **连续云投放**。 满怀信心地跨代码分支和开发团队以连续的方式从开发一直到UAT一直到生产。

## 第三方服务

此部分总结了云基础架构项目上Adobe Commerce的主要第三方服务和工具。 有关详细信息，请参阅&#x200B;_云指南_&#x200B;中的[技术栈栈](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/tech-stack.html)。

- **Fastly CDN**：当客户访问您的网站和商店时，请求点击Fastly可更快地加载缓存页面。 Fastly WAF还提供DDoS保护服务。

- **New Relic**：提供应用程序和操作环境的完整视图。 New Relic允许您将移动和浏览器应用程序中的关键量度与支持的服务、数据存储和主机结合使用，以便您能够全面优化性能并确保每个计划都取得成功。

- **编辑器**：管理Adobe Commerce中的依赖项和升级，并提供有关包含的包的上下文、包的用途以及它们如何组合在一起。

- **Git**：提供源代码管理。 Git允许本地分支、方便的暂存区域以及多个工作流程，并进行自动构建和部署，以实现高效的快速开发和持续部署。

- **Platform-as-a-Service (PaaS)**：提供预配置的基础结构，包括PHP、MySQL、Redis、[!DNL RabbitMQ]以及OpenSearch或Elasticsearch技术。

- **AWS或Azure云托管**：支持基础基础设施即服务(IaaS)，为在线销售和零售提供可扩展且安全的环境。
