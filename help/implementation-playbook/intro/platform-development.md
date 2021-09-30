---
title: 平台开发原则
description: 了解使用Adobe商务时的基本平台开发原则。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# 平台开发原则

在本手册中，我们更深入地研究了Adobe商务开发的一些主要标准，包括：

- 功能和技术范围与开发过程相适应
- 与MVC架构保持一致的开发最佳实践
- 架构考虑事项，包括GRA
- 针对脚本和漏洞攻击的安全标准
- 扩展开发最佳实践
- 与REST、SOAP和GraphQL的Web API集成
- 编码和基础架构的性能改进
- 测试工具、策略和方法

虽然某些解决方案实施者在涉及整个实施项目中使用的方法体系、流程和工具时可能有自己的偏好，但本手册重点介绍可在大多数实施中共享的公认最佳实践和方法。

与任何大型IT项目一样，Adobe商务构建于编码标准之上，这些标准利用了底层技术（例如PHP/Zend、Symfony、JavaScript、jQuery和HTML）的最佳实践和标准化，以及Adobe商务编码标准中已建立的标准。 遵循这些标准是消除错误和提高自定义构建代码的质量和可维护性的绝对必要条件。

## Adobe云基础架构上的商务

Adobe云基础架构上的Adobe商务是用于云商务软件的受管自动托管平台。 云基础架构上的Adobe商务附带了多种其他功能，使其与本地Adobe商务和Magento Open Source实施不同：

![Adobe商务组件信息](../../assets/playbooks/commerce-cloud.svg)

云基础架构上的Adobe商务提供了预配置的基础架构，其中包括PHP、MySQL、Redis、RabbitMQ和Elasticsearch技术；基于Git的工作流，具有自动构建和部署操作，每次在Platform as a Service(PaaS)环境中推送代码更改时，都可进行高效的快速开发和持续部署；高度可定制的环境配置文件和工具；和AWS托管，为在线销售和零售提供可扩展且安全的环境。

![Adobe商务组件信息](../../assets/playbooks/cloud-tech-stack.svg)
