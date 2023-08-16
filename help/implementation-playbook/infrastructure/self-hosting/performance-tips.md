---
title: 自托管Adobe Commerce性能提示
description: 了解自托管性能提示以及要考虑的概念和最佳实践。
landing-page-description: 了解自行托管Adobe Commerce时要考虑的一些性能提示概念和事项。
short-description: 了解自行托管Adobe Commerce的策略和性能提示概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
feature: Install
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# 自托管Adobe Commerce性能提示

使用灵活而强大的电子商务平台并不意味着您必须牺牲性能。 自Adobe Commerce创建以来，核心应用程序得到了大量改进。 在版本2.5.4中，Adobe Commerce工程团队执行了一项设置测试，以对应用程序进行基准测试。 测试结果表明，Adobe Commerce能够处理超过2.4亿个SKU的大型目录，API请求时间平均为300毫秒，并且每小时的页面查看次数和订单数非常惊人，达到200万次页面查看次数和208,000次订单。

转到以下位置查看最新的基准测试结果 [Experience League- Adobe Commerce — 实施行动手册 — 基准](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

要尽可能优化项目，在向项目添加自定义项和增加复杂性时，请遵循这些标准。

以下部分包含有关如何优化自托管实施时要考虑的主题和建议。

## 清漆

清漆是具有缓存的HTTP反向代理。 尽管这看起来很复杂，但结果却是快速的响应，以帮助确保比从源中获取项目更快返回请求。 运行没有某些版本的Varnish的Adobe Commerce网站将导致页面加载速度和其他关键量度缓慢。 油漆可能有点难以设置和管理，但我们在Experience League中确实有这个主题 [配置清漆](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} 以更好地了解它与Adobe Commerce的使用情况。 另一种方法是使用基于云的解决方案。 虽然要考虑的因素很多，但最终选择了Fastly作为Adobe Commerce云端解决方案。 它是基于云的Fastly的一个版本，它使用VCL和许多清漆。

要找到最适合您的应用程序、配置、预算和技术能力的解决方案非常困难。 使用基于云的选项，可让所有硬部件消失，如在管理、配置、服务器和其他基础架构组件方面。 由于其性能、可扩展性、吞吐量以及其他许多关键指标，AWS被Adobe Commerce on cloud团队选为其解决方案。

通过为您的项目选择有关Varnish的良好解决方案，您将自己设置为为客户获得最佳性能，并使商业应用程序不必再努力工作。

## CDN

在Varnish成为您的Adobe Commerce项目宝贵资源的同时，下一个顺理成章的是CDN。 除了您的涂漆之外，CDN还可以为CSS、页面资产（如图像）提供缓存实例，以帮助减少进入Adobe Commerce应用程序的带宽。 它可以缓存GraphQL响应，进一步发挥Headless Adobe Commerce站点的优势。 某些CDN提供图像优化、Web应用程序防火墙和其他功能。

Adobe Commerce on cloud选择将Fastly用作其Varnish缓存，但也用作其CDN。 这个单一解决方案提供了大量功能，可为Adobe Commerce on cloud客户提供绝佳体验。 您可以阅读Experience League中的Fastly服务概述 [Fastly服务概述](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

CDN可为Adobe Commerce项目提供优化且安全的交付内容。 如果这不是您的项目的必需组件，则当您的网站趋于成熟且访客量增加时，应考虑这一点。 通过提供CDN，您可以延迟向基础架构添加其他硬件或扩展现有基础架构，这是因为从每个请求中删除了负载。

## 禁用模块

应考虑禁用未使用的模块，但不要掉以轻心。 对于某些请求，此技术的确会减少一些开销和处理时间，但会产生一些需要考虑的副作用。 有时，开发人员在创建功能时通常会假设模块可用。 这通常是安全的，除非他们选择使用在已禁用的模块中找到的某些类。

禁用模块（如本机“新闻稿”）是一种相当常见的事件。 当商店所有者拥有一家第三方公司管理其新闻通讯时，情况尤其如此。 当安装了第三方模块并且出于某种原因他们决定使用新闻稿中的类时，可能出现问题。 在某些初始安装和测试过程中，可能会捕获到这种意外依赖关系，但随后您将被迫决定是否要保留此第三方模块，启用新闻稿，然后进行回归测试以查找引入的任何异常行为。 或者，您是否找到替代该第三方模块的产品。 这两个决定都伴随着风险、时间以及可能的错误。

在禁用未使用的模块之前，请确保您没有任何测试，例如设备、 [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} 负载测试或可能受影响的API请求。

## 要求每个拉取请求都遵循Adobe Commerce和PHP编码标准

Adobe Commerce有一套 [编码标准](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. 这些功能有助于确保遵循类似的模式、样式和预期设计，而不管软件开发类型如何。 在向Adobe Commerce代码库贡献内容时，这是一项要求。 但是，如果您选择遵循此自定义开发方法，将为所有开发人员（包括当前和未来开发人员）奠定坚实的基础。 在要求所有拉取请求都传递代码标准时，有助于确保每个人都可以理解和期待相同的一致开发模式。

为了配合Adobe Commerce的编码标准，使用的另一个基础是PHP基础编码标准。 开发人员指南中应明确定义要求您遵循的标准以及任何可接受的偏差。 但是，回退到可在以下位置找到的公开维护的指南： [PHP-FIG](https://www.php-fig.org){target="_blank"}.

对执行PSR-1和PSR-12的坚定立场。 确保为项目贡献内容的开发人员遵循这些规则有助于确保没有结构异常的文件和模式。 这还有助于确保未来的开发人员能够快速阅读并了解他们审核的代码。 您越是遵循这些模式和编码标准，未来开发工作应该越容易阅读，实施速度就越快。

## 在每次部署后运行负载测试

在每次部署后执行负载测试可能显得过度。 但是，如果遵循此方法，则可以跟踪和缓解新引入的功能导致性能下降的机会。

除了检测新代码的性能下降之外，了解网站关键量度的历史引用还可以帮助您深入了解何时启用新工具或更改基础架构。 例如，在付费给托管公司来扩大环境规模并希望性能提高幅度达到预期之前，您可以使用新配置设置一个暂存环境，然后运行负载测试以查看实际结果。

这些测试可以自动进行，并且是CI/CD管道的一部分。 因此，您还可以设置规则来记录结果，如果偏离基准太多，则可能会阻止特征合并。 此数据的用例数量是无限的，但如果不启动此过程，您可能会永远无法实现其潜力。

Adobe Commerce对此主题有很好的写法，可在Experience League中找到 [性能测试提示](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
