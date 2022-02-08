---
title: 平台工具
description: 为Adobe Commerce实施选择推荐的平台工具。
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 平台工具

要让电子商务网站不受干扰地运行，必须仔细思考并严格测试哪些方面。 您不仅必须确定适当的解决方案来解决站点的各个方面（从数据存储和编程到缓存和安全），还需要适当的流程来确保平台的交付，该平台运行顺利，并且可以高效构建和优化。

本节不仅介绍了在许多Adobe Commerce实施中经过测试和完善的工具、解决方案、流程和方法，还提供了我们的建议，哪些解决方案最适合特定的业务需求和目标。

下表包含我们推荐的可在Adobe Commerce中用于提高平台性能的解决方案：

| 用途 | 工具 |
|------------------------------------------|-------------------------|
| 数据库 | MySQL、MariaDB、Percona |
| 编程语言 | PHP、JS、HTML、更少CSS |
| 集成开发环境(IDE) | Eclipse、PHPStorm |
| Web服务器 | Nginx、Apache |
| 缓存服务 | 雷迪斯，清漆 |
| 搜索服务 | Elasticsearch |
| 消息队列服务 | RabbitMQ |
| 安全扫描工具 | 声纳库布、扎普 |

## 数据库

我们根据品牌需求使用了三种不同的工具。 如果您不希望您的存储处理极端负载， MySQL将是与Adobe Commerce数据库一样的优秀基准解决方案。

MariaDB更注重社区，对于更关心功能而非纯粹性能的用户而言，它的工作效果更好。 MariaDB支持大型数据库引擎阵列、磁盘加密、复杂的水平互连和扩展功能，这对于大型Adobe Commerce存储区来说可能很有趣。

Percona是MySQL的分支，以性能和峰值负载处理为中心。 如果您需要更高的生活质量和DevOps功能，请选择MariaDB。 如果您的目标是在大型数据集中获得高负载性能，请转到Percona。

## 编程语言

Adobe Commerce是基于PHP的应用程序，最新版本始终与最新的稳定PHP版本兼容(例如，Adobe Commerce版本2.4建议使用PHP 7.4)。 为了获得更高的安全性和性能，在配置PHP时需要考虑以下几个因素，以便在请求处理时获得最大的速度和效率。 Adobe Commerce Web店面是使用HTML、JavaScript和LESS CSS预处理器构建的。

## Web服务器

Adobe Commerce完全支持Nginx和Apache Web服务器。 Adobe Commerce为以下两项提供了建议的配置文件示例：

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Nginx示例包含用于提高性能的设置，并且经过设计，因此无需重新配置。

## 缓存服务

Adobe Commerce提供了许多用于存储缓存和会话数据的选项，包括Redis、Memcache、文件系统和数据库。 对于具有多个Web节点的设置，最佳选项是“Redis”。

我们强烈建议将清漆用作存储的全页缓存服务器。 Adobe Commerce为清漆分发了一个样例配置文件，其中包含所有推荐的性能设置。

## 搜索服务

对于Adobe Commerce版本2.4及更高版本，必须将所有安装配置为使用Elasticsearch作为目录搜索解决方案。 Elasticsearch提供对目录中产品的快速和高级搜索。 Elasticsearch对于2.4之前的版本是可选的，但建议使用。

## 消息队列服务

消息队列提供了一种异步通信机制，其中消息的发送者和接收者不会相互联系。 RabbitMQ是一个开源报文代理，提供可靠、高可用、可扩展和可移植的报文传送系统。

## 安全工具

的 [Adobe Commerce安全扫描工具](https://docs.magento.com/user-guide/magento/security-scan.html) 使您能够定期监控您的商店网站，并接收已知安全风险、恶意软件和过期软件的更新。 通常，在开始用户接受测试(UAT)时，您便会开始使用此工具。 除了Adobe Commerce安全扫描工具(该工具对Adobe Commerce的所有实施和版本都免费可用)之外，在CI/CD过程和每个版本发布之前，还可以使用其他选项。

SonarQube是一个开源质量管理平台，旨在分析和衡量代码的技术质量。 SonarQube不仅提供了代码错误、语法错误和漏洞的完整报告，还提供了修复代码的建议和示例。 SonarQube非常适合在CI/CD环境中使用，作为一种工具，能够在代码部署前分析代码。

Zed Attack Proxy(ZAP)是一种免费的安全测试工具，由全球成千上万的笔试人员使用。 ZAP是由OWASP开发的，是人工安全测试中最常用的工具之一。
