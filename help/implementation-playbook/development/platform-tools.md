---
title: 平台工具
description: 选择适用于Adobe Commerce实施的推荐平台工具。
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
feature: Configuration
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 平台工具

要保持一个电子商务网站不受干扰地运行，必须仔细考虑并严格测试这些方面，这些方面不乏缺缺。 您不仅必须确定正确的解决方案来处理站点的各个方面 — 从数据存储和编程到缓存和安全性 — 而且还需要正确的过程来确保提供一个能够平稳运行并且能够高效构建和优化的平台。

本节不仅介绍在多个Adobe Commerce实施中经过测试和完善的工具、解决方案、流程和方法，还介绍我们对于哪些解决方案最符合特定业务需求和目标的建议。

下表包含我们推荐的解决方案，可以在Adobe Commerce中使用这些解决方案来提高平台性能：

| 用途 | 工具 |
|------------------------------------------|-------------------------|
| 数据库 | MySQL、MariaDB、Percona |
| 编程语言 | PHP、JS、HTML，更少CSS |
| 集成开发环境(IDE) | Eclipse， PHPStorm |
| Web服务器 | Nginx、Apache |
| 缓存服务 | 雷迪斯，清漆 |
| 搜索服务 | Elasticsearch |
| 消息队列服务 | [!DNL RabbitMQ] |
| 安全扫描工具 | SonarQube， ZAP |

## 数据库

我们根据品牌的需求使用三种不同的工具。 如果您不希望您的存储处理极端负载，那么MySQL是作为Adobe Commerce数据库的绝佳基线解决方案。

MariaDB更加以社区为中心，对于更关注功能而非单纯性能的用户来说效果更好。 MariaDB支持大量数据库引擎、磁盘加密、复杂的水平互连和扩展功能，这些功能对于大型Adobe Commerce存储可能很有用。

Percona是MySQL的一个分支，它以性能和峰值负载处理为中心。 如果您需要更高的生活质量和DevOps功能，请选择MariaDB。 如果您的目标是在大规模数据集中获得高负载性能，请转到Percona。

## 编程语言

Adobe Commerce是一个基于PHP的应用程序，并且最新版本始终与最新稳定PHP版本兼容(例如，Adobe Commerce版本2.4建议使用PHP 7.4)。 要获得更高的安全性和性能，在配置PHP以获得最大请求处理速度和效率时，需要考虑以下几个因素。 Adobe Commerce Web店面是使用HTML、JavaScript和LESS CSS预处理程序构建的。

## Web服务器

Adobe Commerce完全支持Nginx和Apache Web服务器。 Adobe Commerce为以下两种工具提供了示例推荐配置文件：

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Nginx示例包含用于提高性能的设置，并且设计得只需很少的重新配置。

## 缓存服务

Adobe Commerce提供多种选项来存储缓存和会话数据，包括Redis、Memcache、文件系统和数据库。 对于具有多个Web节点的设置，Redis是最佳选项。

我们强烈建议使用Varnish作为商店的全页缓存服务器。 Adobe Commerce分发一个用于Varnish的示例配置文件，其中包含所有推荐的性能设置。

## 搜索服务

对于Adobe Commerce版本2.4及更高版本，必须将所有安装配置为使用Elasticsearch或OpenSearch作为目录搜索解决方案。 Elasticsearch功能可对目录中的产品进行快速和高级搜索。 对于2.4之前的版本，Elasticsearch是可选的，但建议使用。

## 消息队列服务

消息队列提供了一种异步通信机制，在这种机制中，消息的发送者和接收者不会相互联系。 [!DNL RabbitMQ]是一个开源消息代理，可提供可靠、高可用、可扩展和可移植的消息传递系统。

## 安全工具

通过[Adobe Commerce安全扫描工具](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)，您可以定期监视商店网站并接收已知安全风险、恶意软件和过期的软件的更新。 通常，在开始用户验收测试(UAT)时即开始使用此工具。 Adobe Commerce安全扫描工具免费且适用于Adobe Commerce的所有实施和版本，除此之外，您还可以在CI/CD流程期间和每个版本之前使用其他选项。

SonarQube是一个开源质量管理平台，旨在分析和衡量代码的技术质量。 SonarQube不仅提供了有关代码错误、语法错误和漏洞的完整报告，而且还提供了有关修复代码的建议与示例。 SonarQube非常适合于在CI/CD环境中用作能够在部署它之前分析代码的工具。

Zed Attack Proxy (ZAP)是一种免费的安全测试工具，全球成千上万的笔测试者都使用它。 ZAP是由OWASP开发的，是手动安全测试中最常用的工具之一。
