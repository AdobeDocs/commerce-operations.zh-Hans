---
title: 本地基础设施
description: 了解Adobe Commerce内部部署基础架构和第三方云服务。
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
source-git-commit: a253da8cfe95083d1df76d3253aaa424b78a4865
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Adobe Commerce内部基础设施

启动新的Adobe Commerce实施或将现有的内部部署Adobe Commerce实施移至云的动机众多，但最常见的战略驱动因素是降低资本支出、降低持续成本、提高可扩展性和弹性、缩短上市时间以及提高安全性和合规性。

下图显示了在AWS基础架构上部署Adobe Commerce内部部署的参考架构。 其他云提供商，如Azure、Google云和阿里巴巴云，都有类似的基础设施设计和相应服务。

![显示关于第三方云服务的自托管Adobe Commerce基础架构的图表](/help/assets/playbooks/on-premises-infrastructure.svg)

让我们更深入地了解上述基础架构各个方面的角色和功能：

1. Amazon路由53提供DNS配置。

1. AWS WAF是一个Web应用程序防火墙，可保护Adobe Commerce免受常见Web漏洞攻击。

1. Amazon CloudFront是一个快速内容交付网络(CDN)，可加快静态和动态Web内容的分发。

1. 第一个弹性负载平衡应用程序负载平衡器在多个可用区的AWS自动缩放组中的清漆实例之间分配流量。

1. 清漆缓存是Web应用程序加速器缓存HTTP反向代理。 推荐使用通过AWS市场提供的企业版，因为它具有更好的功能来支持云后端和跨动态主机的缓存清除。

1. 第二个弹性负载平衡应用程序负载平衡器在多个可用区中的Adobe Commerce实例的AWS自动缩放组中分发来自清漆缓存的流量。

1. 在Amazon EC2实例上安装最新版本的Magento Open Source或Adobe Commerce。 安装由Adobe Commerce应用程序、Nginx Webserver和PHP组成。 构建Amazon计算机图像(AMI)以在自动缩放组中启动新实例。

1. AmazonElasticsearch服务是用于Adobe Commerce目录搜索的托管Elasticsearch服务。

1. Amazon ElastiCache for Redis为数据库提供了缓存层。

1. 使用Amazon Aurora或AmazonRDS简化数据库管理(包括高可用性和多主控配置)。

1. EFSMount Target有助于将Amazon弹性文件系统(AmazonEFS)映射到清漆和Adobe Commerce实例。

1. 使用Amazon EFS跨清漆访问共享配置，跨Adobe Commerce实例访问共享媒体资产。

## 云服务

除了提供支持技术平台以在Adobe Commerce环境的AWS上启用DevOps流程外，AWS还提供了一系列服务，这些服务可以提供（在没有的情况下）或增强您现有的软件配置管理(SCM)解决方案。 这包括AWSCodeCommit、AWSCodeBuild、AWSCodePipeline和AWSCodeDeploy，它们允许进行受管的源代码控制、构建、连续集成/连续部署(CI/CD)和部署服务。

## 云迁移

Adobe Commerce迁移到AWS的价值主张因提供了一些可提供运营洞察和灵活性的服务而得到进一步增强。 我们的意思是，对平台的运营洞察不仅从技术角度（例如，每小时请求数），还从业务运营角度（例如，每小时订单数），特别是当这两组数据可以结婚时。 这可以近乎实时地了解促销活动效果、平台运营成本以及几乎无限数量的其他指标。

Adobe Commerce设置到AWS后，可以使用云中提供的完全托管的替代方案替换特定的应用程序依赖关系。 例如，许多应用程序的数据库可以轻松替换为Amazon关系数据库服务(AmazonRDS)，而不是直接在EC2实例上托管关系数据库。 此策略的好处是，无差别组件的运营责任可以卸载到AWS，而无需对核心应用程序进行重大更改。

在AWS上运行Adobe Commerce(Magento Open Source版本和Adobe Commerce版本)时，可使用多个部署选项。 最合适的选择取决于您对成本、规模、可用性和灵活性的要求，以及贵组织的AWS和Adobe Commerce技能。

{{$include /help/_includes/hosting-related-links.md}}
