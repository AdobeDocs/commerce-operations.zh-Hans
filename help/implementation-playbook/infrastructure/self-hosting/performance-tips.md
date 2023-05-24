---
title: 自托管Adobe Commerce性能提示
description: 了解自托管性能提示想法以及要考虑的概念和最佳实践。
landing-page-description: 了解自行托管Adobe Commerce时的一些性能提示概念和注意事项。
short-description: 了解自行托管Adobe Commerce的策略和性能提示概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# 自托管Adobe Commerce性能提示

使用灵活且功能强大的电子商务平台并不意味着您必须牺牲性能。 自Adobe Commerce推出以来，核心应用程序已得到大量改进。 在版本2.5.4中，Adobe Commerce工程团队执行了一项设置测试，以对应用程序进行基准测试。 测试结果表明，Adobe Commerce能够处理超过2.4亿个SKU的大型目录，API请求时间平均为300毫秒，并且每小时的页面查看次数和订单数非常惊人，达到了200万次页面查看次数和208,000次订单。

转到以下位置查看最新的基准测试结果： [Experience League- Adobe Commerce — 实施行动手册 — 基准](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

要尽可能优化项目，请在向项目添加自定义项和额外复杂性时遵循这些标准。

以下部分介绍了有关如何优化自托管实施应考虑的主题和建议。

## 清漆

清漆是具有缓存的HTTP反向代理。 尽管这看起来很复杂，但结果却是快速响应，以帮助确保比从源中获取项目时更快地返回请求。 在没有某些版本的Varnish的情况下运行Adobe Commerce网站将导致页面加载和其他关键量度速度变慢。 涂漆可能有点难以设置和管理，但我们在Experience League中也有这个主题 [配置清漆](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} 以更好地了解它与Adobe Commerce的使用情况。 替代方法是使用基于云的解决方案。 虽然需要考虑的因素很多，但最终选择了Fastly作为Adobe Commerce云端解决方案。 它是基于云的Fastly的一个版本，使用VCL和许多清漆面。

要找到最适合您的应用程序、配置、预算和技术能力的解决方案非常困难。 使用基于云的选项可让所有硬部件消失（在考虑管理、配置、服务器和其他基础架构组件时）。 由于其性能、可扩展性、吞吐量以及许多其他关键指标，它被Adobe Commerce on cloud团队选为其解决方案。

通过为您的项目选择有关Varnish的良好解决方案，您将自己设置为为客户获得最佳性能，并避免商业应用程序不必要地更努力工作。

## CDN

随着Varnish对您的Adobe Commerce项目来说是一项宝贵的资产，下一行是CDN。 除了涂漆之外，CDN还可以为CSS、页面资产（如图像）提供缓存实例，以帮助减少进入Adobe Commerce应用程序的带宽。 它可以缓存GraphQL响应，以进一步发挥Headless Adobe Commerce站点的优势。 某些CDN提供图像优化、Web应用程序防火墙和其他功能。

Adobe Commerce on cloud选择将Fastly用作其Varnish缓存，但也用作其CDN。 此单一解决方案提供了大量功能，可为Adobe Commerce on cloud客户提供卓越的体验。 您可以阅读Experience League中的Fastly服务概述 [Fastly服务概述](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

CDN可为Adobe Commerce项目提供优化且安全的投放内容。 虽然这可能不是项目的必需组件，但在网站日趋成熟且访客数量增加时，应将此视为必需组件。 通过提供CDN，您可以延迟向基础架构添加其他硬件或扩展现有基础架构，因为每个请求中移除了负载。

## 禁用模块

应考虑禁用未使用的模块，但不要轻率地这样做。 此技术的确为某些请求减少了一些开销和处理时间，但有一些副作用需要考虑。 有时，开发人员会假设在创建功能时模块可用。 这通常是安全的，除非他们选择使用在已禁用的模块中找到的某些类。

禁用模块（如本机“新闻稿”）是一种相当常见的事件。 当商店所有者拥有一家管理其新闻通讯的第三方公司时，情况尤其如此。 当安装了第三方模块并且出于某种原因他们决定使用新闻稿中的类时，可能会出现此问题。 在某些初始安装和测试过程中，可能会发现这种意外依赖关系，但随后您将不得不决定是否要保留此第三方模块、启用新闻稿，然后进行回归测试网站，以查找引入的任何奇怪行为。 或者，您是否找到替代该第三方模块的产品。 这两个决定都伴随着风险、时间以及可能的错误。

在禁用未使用的模块之前，请确保您没有任何测试，例如设备、 [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} 负载测试或可能受影响的API请求。

## 要求每个拉取请求都遵循Adobe Commerce和PHP编码标准

Adobe Commerce有一套 [编码标准](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. 这些功能有助于确保遵循类似的模式、样式和预期设计，而不管软件开发类型如何。 在向Adobe Commerce代码库贡献内容时，这是一项要求。 但是，如果您选择遵循此自定义开发方法，将为当前和未来的所有开发人员奠定坚实的基础。 在要求所有拉取请求都传递代码标准时，有助于确保每个人都可以了解和期望获得相同的一致开发模式。

为了配合Adobe Commerce的编码标准，使用的另一个基础是PHP基础编码标准。 它应在开发人员指南中明确定义，要求您遵循的标准以及任何可接受的偏差。 但是，后备指南应位于以下公开维护的指南中 [PHP-FIG](https://www.php-fig.org){target="_blank"}.

对执行PSR-1和PSR-12的坚定立场。 确保为项目贡献内容的开发人员遵循这些规则有助于确保没有结构奇怪的文件和模式。 这还有助于确保未来的开发人员能够快速阅读并了解他们正在审阅的代码。 您越接近这些模式和编码标准，意味着未来的开发工作应该更容易阅读，并且实施得更快。

## 每次部署后运行负载测试

在每次部署后执行负载测试可能显得过度。 但是，如果遵循此方法，则可以跟踪和缓解新引入功能导致性能下降的机会。

除了检测新代码的性能下降外，拥有网站关键量度的历史引用还有助于深入了解何时启用新工具或更改基础架构。 例如，在向托管公司付费以扩大环境规模并希望您能获得预期的性能提升之前，您可以使用新配置设置暂存环境，然后运行负载测试以查看实际结果。

这些测试可以自动进行，并且是CI/CD管道的一部分。 因此，您还可以制定规则来记录结果，如果偏离标准太多，则可能会阻止特征合并。 此数据的用例数量是无限的，但如果不启动此过程，您可能无法实现其潜力。

Adobe Commerce对此主题有很好的描述，可在Experience League中找到 [性能测试提示](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
