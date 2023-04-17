---
title: 自托管Adobe Commerce性能提示
description: 了解自托管性能提示的想法和概念以及需要考虑的最佳实践。
landing-page-description: 了解自行托管Adobe Commerce时需要考虑的一些性能提示概念和事项。
short-description: 了解自行托管Adobe Commerce的策略和性能提示概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 66abe9f234aa44f7e07cc024607eeb6591a99d07
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 0%

---


# 自托管Adobe Commerce性能提示

使用灵活且功能强大的电子商务平台并不意味着您必须牺牲性能。 自Adobe Commerce创建以来，核心应用程序已得到多项改进。 在版本2.5.4中，Adobe Commerce工程团队执行了一组测试，以对应用程序进行基准测试。 测试结果表明，Adobe Commerce能够处理超过2.4亿个SKU的大型目录，API请求时间平均为300毫秒，并且每小时的页面查看次数和订单数量是惊人的，达到200万页面查看次数和每小时20.8万个订单。

通过标题转到 [Experience League- Adobe Commerce — 实施手册 — 基准](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

为了尽可能保持最佳状态，请在为项目添加自定义设置和额外的复杂性时遵循这些标准。

以下部分涵盖要考虑的主题以及有关如何优化自托管实施的建议。

## 清漆

清漆是带有缓存的HTTP反向代理。 尽管这看起来很复杂，但结果却是快速响应，以帮助确保返回请求的速度比从源中获取项目的速度要快。 如果运行Adobe Commerce站点时没有某些版本的清漆，则页面加载速度会较慢，并且会出现其他关键量度。 清漆设置和管理自己可能会有点困难，不过我们在Experience League中确实有这个主题 [配置清漆](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} 以更好地了解它在Adobe Commerce中的用法。 另一种方法是使用基于云的解决方案。 尽管有很多问题需要考虑，但Fastly被选为云上Adobe Commerce的解决方案。 它是Fastly的云版，使用VCL和许多面漆。

很难找到最适合您的应用程序、配置、预算和技术能力的解决方案。 使用基于云的选项可以使所有硬部件消失，只要考虑管理、配置、服务器和其他基础架构组件。 由于其性能、可扩展性、吞吐量以及许多其他关键量度，云团队中的Adobe Commerce选择了它作为解决方案。

通过为您的项目选择关于清漆的良好解决方案，您可以为客户设置最佳性能，并避免商务应用程序比必要的工作更努力。

## CDN

除了清漆是您的Adobe Commerce项目的宝贵资产外，下一个还是CDN。 除了清漆之外，CDN还可以为CSS、页面资产（如图像）提供缓存实例，以帮助减少进入Adobe Commerce应用程序的带宽。 它可以缓存GraphQL响应，进一步提升无头Adobe Commerce网站的优势。 某些CDN提供图像优化、Web应用程序防火墙和其他功能。

Adobe Commerce on cloud选择使用Fastly作为其Quest缓存，也作为其CDN。 这个单一解决方案提供了众多功能，可为云客户上的Adobe Commerce提供绝佳体验。 您可以在Experience League中阅读Fastly Services概述 [Fastly Services概述](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

CDN为Adobe Commerce项目提供了优化且安全的交付内容。 如果您的项目可能不需要使用此组件，则应将其视为网站日益成熟且访客数量增加所致。 通过提供CDN，您可以延迟向基础架构添加其他硬件，或由于从每个请求中删除了负载而扩展现有基础架构。

## 禁用模块

应当考虑禁用未使用的模块，但不要轻率地这样做。 此技术确实减少了某些请求的开销和处理时间，但也有一些副作用需要考虑。 有时，开发人员会假设某个模块在创建功能时可用。 这通常是安全的，除非他们选择使用在已禁用的模块中找到的某些类。

禁用模块（如本机“新闻稿”）是相当常见的事件。 当商店所有者拥有管理其新闻稿的第三方公司时，尤其如此。 如果安装了第三方模块并且出于某些原因，他们决定使用新闻稿中的类，这可能会导致问题。 这种意外依赖关系可能会在某些初始安装和测试期间被捕获，但之后您将被迫决定是否要保留此第三方模块、启用新闻稿，然后回归测试网站，以查找引入的任何奇数行为。 或者，您是否找到第三方模块的替换。 这两项决定都带来风险、时间，可能还有错误。

在禁用未使用的模块之前，请确保您没有任何测试，例如设备、 [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} 负载测试或可能受到影响的API请求。

## 要求对每个拉取请求都遵循Adobe Commerce和PHP编码标准

Adobe Commerce [编码标准](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. 这些功能有助于确保无论何种软件开发类型，都遵循相似的模式、样式和预期设计。 如果要满足这一基本要求，请在参与Adobe Commerce代码库时执行。 但是，遵循此自定义开发方法也为所有开发人员（当前和未来）奠定了坚实的基础。 当要求所有拉取请求传递代码标准时，有助于确保每个人都能够了解和期待相同的一致开发模式。

为了配合Adobe Commerce编码标准，采用的另一个基础是PHP基本编码标准。 在开发人员指南中应明确定义需要遵循的标准以及可接受的任何偏差。 但是，回退应该是位于 [PHP-FIG](https://www.php-fig.org){target="_blank"}.

对遵循PSR-1和PSR-12的坚定立场。 确保为项目做出贡献的开发人员遵循这些规则，有助于确保不存在结构奇怪的文件和模式。 这还有助于确保未来的开发人员能够快速阅读并了解他们正在审阅的代码。 您越接近这些模式和编码标准，就意味着未来开发工作应该更易于阅读和实施。

## 在每次部署后运行负载测试

在每次部署后执行加载测试可能会显得过多。 但是，如果遵循此方法，则可以跟踪和缓解新引入功能导致性能下降的机会。

除了检测到新代码的性能下降外，从您的网站中引用关键量度的历史参考还有助于深入了解何时启用了新工具或更改基础架构。 例如，在向托管公司支付费用以增加您的环境规模并希望您获得预期的性能提升之前，您可以使用新配置来设置暂存环境，并运行负载测试以查看实际结果。

这些测试可以自动进行，并且是CI/CD管道的一部分。 因此，您还可以制定规则来获取结果，如果与范数的偏差过大，则可能会阻止特征合并。 此数据的用例数量是无限的，但如果不启动此过程，您可能永远不会意识到其潜力。

Adobe Commerce对此主题的说明在Experience League中找到 [性能测试提示](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
