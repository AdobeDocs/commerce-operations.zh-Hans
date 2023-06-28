---
title: 平台开发原则
description: 了解使用Adobe Commerce时的基本平台开发原则。
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# 平台开发原则

在本行动手册中，我们深入探讨了Adobe Commerce开发的一些主要标准，包括：

- 符合开发过程的功能和技术范围
- 与MVC架构相一致的开发最佳实践
- 体系结构注意事项，包括GRA
- 针对脚本和漏洞的安全标准
- 扩展开发最佳实践
- Web API与REST、SOAP和GraphQL的集成
- 编码和基础架构的性能改进
- 测试工具、策略和方法

虽然一些解决方案实施者在实施项目中使用的方法、流程和工具方面可能具有自己的偏好，但本行动手册的重点内容是可在大多数实施中共享的公认的最佳实践和方法。

与任何大型IT项目一样，Adobe Commerce构建于编码标准之上，这些标准利用底层技术(例如，PHP/Zend、Symfony、JavaScript、jQuery和HTML)的最佳实践和标准化，以及在Adobe Commerce编码标准中制定的标准。 遵守这些标准绝对是消除错误并提高自定义代码质量和可维护性的必要条件。

## 云基础架构上的Adobe Commerce

云基础架构上的Adobe Commerce是适用于Adobe Commerce软件的托管、自动托管平台。 云基础架构上的Adobe Commerce附带了各种其他功能，这些功能使其有别于内部部署Adobe Commerce和Magento Open Source实施：

![Adobe Commerce组件infographics](../../assets/playbooks/commerce-cloud.svg)

云基础架构上的Adobe Commerce提供了一个预配置的基础架构，包括PHP、MySQL、Redis、 [!DNL RabbitMQ]、和Elasticsearch技术；基于Git的工作流，具有自动构建和部署操作，可实现高效的快速开发和连续部署(每次在Platform as a Service (PaaS)环境中推送代码更改时)；高度可自定义的环境配置文件和工具；以及AWS托管，可为在线销售和零售提供可扩展且安全的环境。

![Adobe Commerce组件infographics](../../assets/playbooks/cloud-tech-stack.svg)
