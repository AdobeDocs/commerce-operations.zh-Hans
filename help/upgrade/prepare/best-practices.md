---
title: 最佳实践
description: 使用Adobe推荐的最佳实践来管理Adobe Commerce和Magento Open Source项目的升级过程。
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---


# 升级的最佳实践

本主题列出了您应采取哪些操作来管理升级Adobe Commerce和Magento Open Source项目的复杂性。 您的团队应从项目开发开始并持续到每个版本时就开始考虑升级事宜。 通过遵循这些最佳实践，升级过程将会更轻松、更快、更便宜。

>[!TIP]
>
>这些建议基于最佳实践，由合作伙伴、商家、Adobe专家和社区提供的影响和有效性证据支持。

## 升级会产生什么影响？

了解决定升级复杂性的变量非常重要。 您必须在每个项目的开头考虑这些变量，而不只是在需要升级时。 项目的开发是确保未来升级顺利进行以及您能够控制完成这些升级所需的工作量的关键。

升级Adobe Commerce实例的工作量取决于以下因素：

- **您是如何构建您的网站的？** 自定义工作量和已安装的第三方模块的数量会极大地影响升级的复杂性。 自定义工作和模块的质量可以决定升级是否顺利进行。

- **是否正在跳过多个版本？** 跳过版本会使下一次升级更复杂，从后续版本升级会使过程更简单、更便宜。

- **您执行哪种升级类型？** 升级到次要版本（例如从2.3.x升级到2.4.0）的范围比升级补丁版本（例如从2.4.2升级到2.4.3）的范围更广。 安全升级是最简单的实施类型。

## 规划升级的最佳实践

如果您正在处理的项目已经在生产中，升级是您提高代码质量和自定义设置以及优化未来升级的一个机会。 你今天投资的时间是长期节省的时间。

如果您为不同的商家管理多个网站，最佳方法是创建一个基本实例，该实例具有您通常使用的主要功能和自定义设置。 使用此基本实例作为测试站点来完成升级，然后对其他实例执行升级。 通过这种做法，您可以灵活地为不同的客户重复使用自定义模块，并简化跨项目的升级。

如果您的项目处于启用状态，我们建议您运行审核以确定其质量，并了解如何改进该项目以提高升级效率。

### 考虑升级进行开发

从您开始处理项目之后，您应该考虑当前工作对未来升级的影响。 始终遵循Adobe Commerce开发最佳实践，如下所述：

- [开发最佳实践](https://devdocs.magento.com/guides/v2.4/ext-best-practices/bk-ext-best-practices.html)
- [编码标准](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html)

如果您尚未采用Adobe Commerce扩展性平台，请开始采用该平台。 该平台可让您高效地定制流程、集成系统和部署新功能，同时保持SaaS类升级能力。 其功能包括：

- **UI扩展性**. 使用 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/).

- **API扩展性**. 使用 [GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/index.html) 通过演进图形数据模型并直接从图形层执行λ函数来扩展Web API层。

- **Adobe I/O中间件和服务**. 使用Adobe的中间件和一套基于的应用程序连接来将您的系统与Adobe Commerce连接起来 [Adobe I/O](https://www.adobe.io/). 此外，您还可以使用自己在Adobe I/O上运行的业务逻辑覆盖默认行为，从而扩展核心平台功能。

### 计划升级

随着我们不断扩展Adobe Commerce的功能，在最新可用版本上进行开发并在项目计划中定义升级策略至关重要。 这样做有助于您保持安全、合规和最新的最新增强功能，使您能够更快地增长销售，更有效地运营，并在现在和未来保持领先竞争。

为了帮助您计划升级和预算，您应该监控我们的 [发布计划](https://devdocs.magento.com/release). 提前计划团队积压的升级任务。 旨在通过GA完成此工作。

- 使用预发行版本了解每个新版本。 预发布是一般可用性代码，在正式发布两周前，该代码可供Adobe Commerce商家和所有合作伙伴使用。 如果您有多个商店，请使用基础商店上的预发行版，并验证自定义模块和主题是否与其兼容。

- 查看 [升级计划核对清单](https://support.magento.com/hc/en-us/articles/360057968951) ，以帮助您规划升级。

- 计划年初的升级。 您必须预订预算和资源才能完成每次升级。 请记住，升级工作可能因项目而异。 利用您的经验和知识，尽可能准确地制定计划。

- 如果您的升级比我们此处介绍的更费力，我们建议您审核项目并调整环境以减少长期维护。

### 执行升级

应定期在预定预算下进行升级。 我们建议计划在年初进行预先批准的升级，以确保升级按计划进行并按时完成。

评估升级工作：

- 查看 [发行说明](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) 以了解新版本的范围和影响。

- 使用 [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) 以确定在尝试升级到新版本之前必须在自定义代码中修复的潜在问题。

- 如果您使用的是第三方扩展，请验证它们与计划升级到的目标版本的兼容性。

### 升级后测试

测试是升级的阶段，需要最多的时间。 因此，此过程应尽可能自动化。 使用核心测试工具可让您受益。 的 [应用程序测试指南](https://devdocs.magento.com/guides/v2.4/test/testing.html) 提供详细信息。

在转到生产环境之前，请使用暂存环境来测试和验证升级。

使用 **维护页面**. 通过提前准备此页面，您可以与客户进行通信，并通知他们工作正在后台进行。 此页面应该会显示几分钟，但如果遇到问题，您可能需要更长时间使用它。 为维护页面提供适当的内容和设计，即使您的商店不可用，也能为用户提供良好的体验。
