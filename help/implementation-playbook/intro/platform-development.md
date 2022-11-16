---
title: 平台开发原则
description: 了解使用Adobe Commerce时的基本平台开发原则。
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# 平台开发原则

在本手册中，我们更深入地研究了Adobe Commerce开发的一些主要标准，包括：

- 功能和技术范围与开发过程相适应
- 与MVC架构保持一致的开发最佳实践
- 架构考虑事项，包括GRA
- 针对脚本和漏洞攻击的安全标准
- 扩展开发最佳实践
- 与REST、SOAP和GraphQL的Web API集成
- 编码和基础架构的性能改进
- 测试工具、策略和方法

虽然某些解决方案实施者在涉及整个实施项目中使用的方法体系、流程和工具时可能有自己的偏好，但本手册重点介绍可在大多数实施中共享的公认最佳实践和方法。

与任何大型IT项目一样，Adobe Commerce构建于编码标准之上，这些标准利用了底层技术(例如PHP/Zend、Symfony、JavaScript、jQuery和HTML)的最佳实践和标准化，以及Adobe Commerce编码标准中已建立的标准。 遵循这些标准是消除错误和提高自定义构建代码的质量和可维护性的绝对必要条件。

## Adobe Commerce云基础架构

Adobe Commerce on cloud基础架构是Adobe Commerce软件的一个托管、自动托管平台。 Adobe Commerce on cloud基础架构附带了多种其他功能，使其与内部部署的Adobe Commerce和Magento Open Source实施相去甚远：

![Adobe Commerce组件信息图](../../assets/playbooks/commerce-cloud.svg)

云基础架构上的Adobe Commerce提供了预配置基础架构，其中包括PHP、MySQL、Redis、 [!DNL RabbitMQ]、Elasticsearch技术；基于Git的工作流，具有自动构建和部署操作，每次在Platform as a Service(PaaS)环境中推送代码更改时，都可进行高效的快速开发和持续部署；高度可定制的环境配置文件和工具；以及AWS托管，为在线销售和零售提供一个可扩展且安全的环境。

![Adobe Commerce组件信息图](../../assets/playbooks/cloud-tech-stack.svg)
