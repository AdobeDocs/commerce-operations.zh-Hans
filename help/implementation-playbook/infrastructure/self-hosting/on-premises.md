---
title: 内部部署基础架构
description: 了解Adobe Commerce本地基础设施和第三方云服务。
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
source-git-commit: a253da8cfe95083d1df76d3253aaa424b78a4865
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Adobe Commerce内部部署基础架构

启动新的Adobe Commerce实施或将现有的本地Adobe Commerce实施迁移到云的动机很多，但最常见的战略推动因素是减少资本支出、降低持续成本、提高可扩展性和弹性、缩短上市时间以及实现安全性和合规性的改进。

下图显示了用于在AWS基础架构上本地部署Adobe Commerce的参考架构。 其他云提供商，如Azure、Google云和Alibaba云，共享相似的基础架构设计和同类服务。

![显示第三方云服务上自托管Adobe Commerce基础架构的图表](/help/assets/playbooks/on-premises-infrastructure.svg)

让我们更深入地探讨上述基础架构各个方面的角色和功能：

1. Amazon Route 53提供DNS配置。

1. AWS WAF是一种Web应用程序防火墙，可保护Adobe Commerce免受常见的Web攻击。

1. Amazon CloudFront是一个快速内容交付网络(CDN)，可加快静态和动态Web内容的分发。

1. 第一个Elastic Load Balancing应用程序负载平衡器在AWS Auto Scaling组内的多个可用区中跨Varnish实例分发流量。

1. 清漆缓存是Web应用程序加速器缓存HTTP反向代理。 推荐的企业版可通过AWS Marketplace使用，因为它有更好的功能来支持云后端和跨动态主机的缓存清除。

1. 第二个Elastic Load Balancing应用程序负载平衡器将来自Varnish Cache的流量分布到多个可用区中的Adobe Commerce实例的AWS Auto Scaling组中。

1. 在Amazon EC2实例上安装最新版本的Magento Open Source或Adobe Commerce。 安装包括Adobe Commerce应用程序、Nginx Web服务器和PHP。 构建Amazon计算机图像(AMI)以在Auto Scaling组中启动新实例。

1. AmazonElasticsearch服务是用于Adobe Commerce目录搜索的托管Elasticsearch服务。

1. 适用于Redis的Amazon ElastiCache为数据库提供了一个缓存层。

1. 使用Amazon Aurora或AmazonRDS简化数据库管理(包括高可用性和多主控配置)。

1. EFSMount Target有助于将Amazon Elastic File System (AmazonEFS)映射到Varnish和Adobe Commerce实例。

1. 使用Amazon EFS可访问在Adobe Commerce实例中跨清漆的共享配置和共享媒体资源。

## 云服务

除了在您的Adobe Commerce环境周围的AWS上提供支持启用DevOps流程的技术平台外，AWS还提供了一组服务，这些服务可以提供（如果没有）或增强您现有的软件配置管理(SCM)解决方案。 这包括AWSCodeCommit、AWSCodeBuild、AWSCodePipeline和AWSCodeDeploy，后者允许托管源代码控制、生成、连续集成/连续部署(CI/CD)和部署服务。

## 云迁移

将Adobe Commerce迁移到AWS的价值主张通过提供运营洞察力和灵活性的多项服务的可用性得到进一步增强。 我们指的不仅是从技术角度（例如，每小时请求数）和业务运营角度（例如，每小时订单数）对平台的运营洞察，尤其是当两组数据可以结合时。 这近乎实时地了解促销活动效果、平台运营成本以及几乎无限数量的其他指标。

Adobe Commerce设置为AWS时，可以使用云中提供的完全托管替代项替换特定的应用程序依赖项。 例如，许多应用程序的数据库可以轻松替换为Amazon关系数据库服务(AmazonRDS)，而不是直接在EC2实例上托管关系数据库。 此战略的好处是，无需对核心应用程序进行重大更改，即可将无差别组件的运营责任转移到AWS。

在AWS上运行Adobe Commerce(Magento Open Source版本和Adobe Commerce版本)时，可以使用多个部署选项。 最合适的选择取决于您在成本、规模、可用性和灵活性方面的要求，以及贵组织的AWS和Adobe Commerce技能。

{{$include /help/_includes/hosting-related-links.md}}
