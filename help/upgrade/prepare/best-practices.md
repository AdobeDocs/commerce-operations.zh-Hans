---
title: 最佳实践
description: 使用Adobe推荐的最佳实践来管理Adobe Commerce项目的升级过程。
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# 升级的最佳实践

本主题列出了为管理升级Adobe Commerce项目的复杂性而应采取的操作。 您的团队应该从项目开发开始时就开始考虑升级，并持续每个版本。 通过遵循这些最佳实践，升级过程将变得更加简单、快速和廉价。

>[!TIP]
>
>这些建议基于最佳实践，由合作伙伴、商家、Adobe专家和社区提供的影响力和有效性证据提供支持。

## 升级会受到哪些影响？

了解确定升级复杂性的变量很重要。 您必须在每个项目的开头考虑这些变量，而不仅仅是升级的时间。 项目开发是确保未来顺利升级以及您能够控制完成升级所需工作的关键。

升级Adobe Commerce实例的工作量取决于以下因素：

- **您是如何构建网站的？**&#x200B;自定义工作量和安装的第三方模块数严重影响升级的复杂性。 自定义工作和模块的质量可确定升级是否顺利进行。

- **是否跳过多个版本？**&#x200B;跳过发行版本使下一次升级更加复杂，从后续版本升级使升级过程更容易、成本更低。

- **您正在执行哪种类型的升级？**&#x200B;与修补程序版本（例如从2.4.2到2.4.3）之间的升级相比，升级到次要版本（例如从2.3.x到2.4.0）的范围更广。 安全升级是最容易实施的类型。

## 规划升级的最佳实践

如果您正在处理的项目已处于生产状态，则升级是一个契机，可让您提高代码和自定义设置的质量，并优化以适合将来的升级。 您今天投资的时间就是长期节省的时间。

如果您为不同的商家管理多个网站，最好的办法是拥有一个基本实例，其中包含您通常会使用的主要功能和自定义设置。 使用此基本实例作为您的测试站点以完成升级，然后在其他人上执行该升级。 通过此做法，您可以灵活地为不同客户重复使用自定义模块，并简化跨项目的升级。

如果您的项目已上线，我们建议您运行审核以确定其质量，并了解如何改进以提高升级效率。

### 开发时考虑升级

从您开始处理项目的那一刻起，您应该考虑一下将来的升级将如何受到您当前工作的影响。 始终遵循如下所述的Adobe Commerce开发最佳实践：

- [开发最佳实践](https://developer.adobe.com/commerce/php/best-practices/)
- [编码标准](https://developer.adobe.com/commerce/php/coding-standards/)

开始采用Adobe Commerce可扩展性平台（如果尚未采用）。 该平台允许您高效地自定义流程、集成系统和部署新功能，同时保持类似SaaS的可升级性。 其功能包括：

- **UI可扩展性**。 使用[PWA Studio](https://developer.adobe.com/commerce/pwa-studio/)，独立于后端和中间件扩展和改进店面。

- **API可扩展性**。 使用[GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/index.html)通过改进图形数据模型并直接从图形层执行lambda函数来扩展Web API层。

- **Adobe I/O中间件和服务**。 使用Adobe的中间件和基于[Adobe I/O](https://www.adobe.io/)构建的应用程序连接套件将您的系统与Adobe Commerce连接。 此外，您可以通过使用在Adobe I/O上运行的自己的业务逻辑覆盖默认行为来扩展核心平台功能。

### 规划升级

随着我们不断扩展Adobe Commerce的功能，您必须在最新可用版本上进行开发，并在项目计划中定义升级策略，这一点至关重要。 这样做有助于您保持安全、合规并及时了解最新的增强功能，从而让您能够更快地增加销售额、更有效地运营，并在现在和未来保持竞争优势。

为了帮助您规划和预算升级，您应该监视我们的[发布计划](https://devdocs.magento.com/release)。 提前计划团队积压中的升级任务。 旨在用GA完成此工作。

- 使用预发行版本了解每个新版本。 预发行版是通用可用性代码，在通用可用性发布两周前可供Adobe Commerce商家和所有合作伙伴使用。 如果您有多个商店，请使用基础商店中的预发行版，并验证您的自定义模块和主题是否与其兼容。

- 查看Adobe Commerce的[升级计划核对清单](https://support.magento.com/hc/en-us/articles/360057968951)，以帮助您规划升级。

- 计划于年初升级。 您必须预订预算和资源才能完成每次升级。 请记住，升级工作可能会因项目而异。 运用您的经验和知识制定尽可能准确的计划。

- 如果您的升级所花费的工作量大于我们在此处所描述的，我们建议您审核您的项目并调整您的环境以减少长期维护。

### 正在执行升级

升级应定期进行，并根据预先确定的预算进行。 我们建议在年初安排预批准的升级，以确保及时规划和完成升级。

评估升级要完成的工作：

- 请查阅[发行说明](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html)以了解新版本的范围和影响。

- 使用[[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md)识别在尝试升级到新版本之前必须在自定义代码中修复的潜在问题。

- 如果您使用的是第三方扩展，请验证其与计划升级到的目标版本的兼容性。

### Post升级测试

测试是需要花费最多时间的升级阶段。 因此，应尽可能自动执行此过程。 您可以使用核心测试工具受益。 [应用程序测试指南](https://developer.adobe.com/commerce/testing/guide/)提供了详细信息。

在移至生产环境之前，请使用暂存环境来测试和验证升级。

使用&#x200B;**维护页**。 通过提前准备此页面，您可以与客户通信，通知他们后台正在进行工作。 此页面应该会持续显示几分钟，但如果出现问题，您可能需要更长时间才能使用。 为您的维护页面提供适当的内容和设计可为您的用户带来良好的体验，即使您的商店不可用。
