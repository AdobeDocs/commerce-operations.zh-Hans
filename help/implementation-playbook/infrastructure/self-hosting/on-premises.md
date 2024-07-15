---
title: 内部部署基础架构
description: 了解Adobe Commerce本地基础设施和第三方云服务。
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
feature: Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Adobe Commerce内部部署基础架构

启动新的Adobe Commerce实施或将现有的本地Adobe Commerce实施迁移到云的动机非常多，但最常见的战略推动因素是减少资本支出、降低持续成本、提高可扩展性和弹性、缩短上市时间以及实现安全和合规方面的改进。

下图显示了用于在AWS基础架构上部署Adobe Commerce本地的参考架构。 其他云提供商，如Azure、Google云和阿里巴巴云，共享相似的基础架构设计和同类服务。

![显示第三方云服务上自托管Adobe Commerce基础架构的图表](/help/assets/playbooks/on-premises-infrastructure.svg)

让我们更深入地探讨上述基础架构各个方面的角色和功能：

1. Amazon Route 53提供DNS配置。

1. AWS WAF是一种Web应用程序防火墙，可保护Adobe Commerce免受常见的Web攻击。

1. Amazon CloudFront是一个快速内容交付网络(CDN)，可加快静态和动态Web内容的分发。

1. 第一个Elastic Load Balancing应用程序负载平衡器在多个可用区中跨AWS Auto Scaling组中的Varnish实例分配流量。

1. 清漆缓存是Web应用程序加速器缓存HTTP反向代理。 推荐使用AWS Marketplace提供的企业版本，因为该版本具有更好的功能，可支持跨动态主机的云后端和缓存清除。

1. 第二个Elastic Load Balancing应用程序负载平衡器将来自Varnish Cache的流量分布到多个可用区中的Adobe Commerce实例的AWS Auto Scaling组。

1. 在Amazon EC2实例上安装最新版本的Adobe Commerce。 安装包括Adobe Commerce应用程序、Nginx Web服务器和PHP。 构建Amazon计算机图像(AMI)以在Auto Scaling组中启动新实例。

1. AmazonElasticsearch服务是用于Adobe Commerce目录搜索的托管Elasticsearch服务。

1. Amazon ElastiCache for Redis为数据库提供了一个缓存层。

1. 使用Amazon Aurora或AmazonRDS简化数据库管理（包括高可用性和多主机配置）。

1. EFSMount Target有助于将Amazon Elastic File System (AmazonEFS)映射到Varnish和Adobe Commerce实例。

1. 使用Amazon EFS在Adobe Commerce实例中访问跨涂漆的共享配置和共享媒体资源。

## 云服务

除了在您的Adobe Commerce环境周围的AWS上提供支持启用DevOps流程的技术平台之外，AWS还提供了一组服务，这些服务可以提供（如果没有）或增强您现有的软件配置管理(SCM)解决方案。 这包括AWSCodeCommit、AWSCodeBuild、AWSCodePipeline和AWSCodeDeploy，它们允许托管源代码控制、生成、连续集成/连续部署(CI/CD)和部署服务。

## 云迁移

借助多种可提供运营洞察力和灵活性的服务的可用性，进一步增强了将Adobe Commerce迁移到AWS的价值主张。 我们的意思是不仅从技术角度（例如每小时请求数）而且还从业务运营角度（例如每小时订单数）对平台进行运营分析，尤其是当两组数据可以结合时。 这几乎可以实时了解营销活动效果、平台运营成本以及几乎无限数量的其他指标。

在AWS中设置Adobe Commerce，可以将特定的应用程序依赖项替换为云中提供的完全托管替代项。 例如，Amazon关系数据库服务(AmazonRDS)可以轻松取代许多应用程序的数据库，而不是直接在EC2实例上托管关系数据库。 此战略的好处是，可以将无差别组件的运营责任转移到AWS，而无需对核心应用程序进行重大更改。

在AWS上运行Adobe Commerce时，可以使用多个部署选项。 最合适的选择取决于您在成本、规模、可用性和灵活性方面的要求，以及贵组织的AWS和Adobe Commerce技能。

{{$include /help/_includes/hosting-related-links.md}}
