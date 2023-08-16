---
title: 云基础架构概述
description: 了解云基础架构上的Adobe Commerce。
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# 概述

Adobe Commerce本身为AWS上的Adobe Commerce提供了最流行的托管选项之一。 云基础架构上的Adobe Commerce是适用于Adobe Commerce软件的完全托管的自动托管平台。

云基础架构上的Adobe Commerce是一种platform-as-a-service (PaaS)产品，支持快速部署完全可自定义、安全且可扩展的Web店面，以及领先的托管和托管服务基础架构。 它提供了两种具有不同基础架构的计划。 Adobe Commerce Starter最适合具有较低复杂性和较小目录的较小商店。 Adobe Commerce Pro专为更复杂、产品目录更大或流量达到峰值的大型商店而构建。 Adobe Commerce将根据合作伙伴提供的信息确定相应的架构。

Adobe Commerce为云做好准备，具有完全冗余的多云托管基础设施，可提供优化的性能、弹性和弹性可扩展性。 您可以在Fastly的内容交付网络(CDN)上高效地运行您的Commerce平台，并利用New Relic进行监控和管理，您可以保持您的商店环境顺畅运行。

Adobe Commerce提供了现代云计算与SaaS解决方案最常见的所有优势：弹性可扩展性、高弹性和可用性、PCI合规性、全球可用性和自动修补，同时仍保持我们的商家所需的软件定制灵活性。

![在云基础架构上显示Adobe Commerce的架构元素的图表](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## 优点

Adobe Commerce的其他优势包括：

- **针对Adobe Commerce进行优化**. Adobe Commerce开发的构建脚本和服务配置可确保正确调整和配置每个实例，以实现最佳商家性能。

- **一致、安全的版本**. 所有代码部署都基于Git以实现一致性和可重复性，并带有只读生产环境以实现增强的安全性。

- **合作伙伴的灵活性**. 完整的REST API和可编写脚本的命令行界面可确保与外部系统轻松集成以及与现有代码管理工作流的兼容性。

- **灵活的部署工具集**. 可随意快速启动、合并、克隆和拆除无限数量的环境，执行开发任务、QA测试或生产问题诊断。

- **连续云交付**. 满怀信心地跨代码分支和开发团队以连续的方式从开发一直到UAT一直到生产。

## 第三方服务

我们还将看一看让Adobe Commerce的优势成为现实的软件。

![在云基础架构技术栈栈上显示Adobe Commerce的图](../../../assets/playbooks/cloud-tech-stack.svg)

- Fastly CDN：当客户访问您的网站和商店时，请求将按Fastly以更快地加载缓存页面。 Fastly WAF还提供DDoS保护服务。

- New Relic为您提供了应用程序和操作环境的完整视图。 它让您可以将移动和浏览器应用程序中的关键量度与支持的服务、数据存储和主机相结合，以便全面优化性能并确保每个计划都取得成功。

- Composer管理Adobe Commerce中的依赖项和升级，并提供有关包含的包、包的用途以及它们如何组合的上下文。

- Git是您在存储库中的代码。 它允许本地分支、方便的暂存区域以及多个具有自动构建和部署的工作流，以实现高效的快速开发和持续部署。

- Platform-as-a-Service (PaaS)提供预配置的基础架构，包括PHP、MySQL、Redis、 [!DNL RabbitMQ]和OpenSearch或Elasticsearch技术。

- AWS或Azure的云托管为底层基础设施即服务(IaaS)提供支持，后者为在线销售和零售提供可扩展且安全的环境。
