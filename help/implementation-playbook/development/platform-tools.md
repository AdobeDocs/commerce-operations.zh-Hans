---
title: 平台工具
description: 为Adobe Commerce实施选择推荐的平台工具。
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
source-git-commit: ea912c48176fb060e48654d05ae6b533436a2432
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 平台工具

要确保电子商务网站不受干扰地运行，必须仔细考虑并严格测试这些方面，不乏这方面的不足。 您不仅必须确定适当的解决方案来处理站点的各个方面（从数据存储和编程到缓存和安全性），而且还需要适当的流程来确保提供一个既可以顺利运行又可以高效构建和优化的平台。

本节不仅介绍在多种Adobe Commerce实施中经过测试和完善的工具、解决方案、流程和方法，还介绍我们对于哪些解决方案最符合特定业务需求和目标的建议。

下表包含我们推荐的解决方案，可以在Adobe Commerce中使用这些解决方案来提高平台性能：

| 用途 | 工具 |
|------------------------------------------|-------------------------|
| 数据库 | MySQL、MariaDB、Percona |
| 编程语言 | PHP、JS、HTML、更少CSS |
| 集成开发环境(IDE) | Eclipse、PHPStorm |
| Web服务器 | Nginx、Apache |
| 缓存服务 | 雷迪斯，清漆 |
| 搜索服务 | Elasticsearch |
| 消息队列服务 | [!DNL RabbitMQ] |
| 安全扫描工具 | SonarQube， ZAP |

## 数据库

我们根据品牌的需求使用三种不同的工具。 如果您不希望存储处理极端负载，MySQL是作为Adobe Commerce数据库的绝佳基线解决方案。

MariaDB更注重社区，更适合那些更关注功能而不是单纯性能的用户。 MariaDB支持大量数据库引擎、磁盘加密、复杂的水平互连和扩展功能，这些功能对于大型Adobe Commerce存储可能很有用。

Percona是MySQL的一个分支，以性能和峰值负载处理为中心。 如果您需要更高的生活质量和DevOps功能，请选择MariaDB。 如果您的目标是在大规模数据集中获得高负载性能，请转到Percona。

## 编程语言

Adobe Commerce是一个基于PHP的应用程序，并且最新版本始终与最新的稳定PHP版本兼容(例如，Adobe Commerce版本2.4建议使用PHP 7.4)。 为了获得更高的安全性和性能，在配置PHP以获得最大请求处理速度和效率时，需要考虑几个因素。 Adobe Commerce Web店面是使用HTML、JavaScript和LESS CSS预处理程序构建的。

## Web服务器

Adobe Commerce完全支持Nginx和Apache Web Server。 Adobe Commerce为以下两种工具提供了示例推荐配置文件：

- **恩金克斯**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Nginx示例包含用于提高性能的设置，并且设计为只需很少重新配置。

## 缓存服务

Adobe Commerce提供了多种选项来存储缓存和会话数据，包括Redis、Memcache、文件系统和数据库。 对于具有多个Web节点的设置， Redis是最佳选项。

我们强烈建议使用Varnish作为商店的全页缓存服务器。 Adobe Commerce分发一个用于Varnish的示例配置文件，其中包含所有推荐的性能设置。

## 搜索服务

对于Adobe Commerce版本2.4及更高版本，必须将所有安装配置为使用Elasticsearch或OpenSearch作为目录搜索解决方案。 Elasticsearch提供对目录中的产品的快速和高级搜索。 对于2.4之前的版本，Elasticsearch是可选的，但建议使用。

## 消息队列服务

消息队列提供了一种异步通信机制，在这种机制中，消息的发送者和接收者不会相互联系。 [!DNL RabbitMQ] 是一个开源消息代理商，它提供可靠、高可用性、可扩展且便携的消息传递系统。

## 安全工具

此 [Adobe Commerce安全扫描工具](https://docs.magento.com/user-guide/magento/security-scan.html) 使您能够定期监视商店网站，并接收已知安全风险、恶意软件和过时软件的更新。 通常，在开始用户验收测试(UAT)时即开始使用此工具。 Adobe Commerce安全扫描工具免费提供给Adobe Commerce的所有实施和版本，除此之外，您还可以在CI/CD过程中和每个版本之前使用其他选项。

SonarQube是一个开源质量管理平台，旨在分析和衡量代码的技术质量。 SonarQube不仅提供了代码错误、语法错误和漏洞的完整报告，还提供了修复代码的建议与示例。 SonarQube非常适合在CI/CD环境中用作能够在部署它之前分析代码的工具。

Zed Attack Proxy (ZAP)是一种免费的安全测试工具，由全球成千上万的笔测试人员使用。 ZAP是由OWASP开发的，是手动安全测试中最常用的工具之一。
