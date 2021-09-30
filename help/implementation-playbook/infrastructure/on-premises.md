---
title: 本地基础设施
description: 了解Adobe商务的内部基础结构和第三方云服务。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---


# Adobe商务内部部署基础设施

启动新的Adobe商务实施或将现有的内部Adobe商务实施移动到云中的动机很多，但最常见的战略驱动因素是降低资本支出、降低持续成本、提高可扩展性和弹性、缩短上市时间以及提高安全性和合规性。

下图显示了在AWS基础设施上部署Adobe商务的参考架构。 其他云提供商，如Azure、Google Cloud和Alibaba Cloud，共享类似的基础设施设计和相应服务。

![显示第三方云服务上自托管Adobe商务基础架构的图表](../../assets/playbooks/on-premises-infrastructure.svg)

让我们更深入地了解上述基础架构各个方面的角色和功能：

1. Amazon路由53提供DNS配置。

1. AWS WAF是一个Web应用程序防火墙，可保护Adobe商务免受常见Web漏洞攻击。

1. Amazon CloudFront是一个快速内容交付网络(CDN)，可加快静态和动态Web内容的分发。

1. 第一个Elastic Load Balancing应用程序负载平衡器在多个可用区的AWS Auto Scaling组中跨Rikest实例分配流量。

1. 清漆缓存是Web应用程序加速器缓存HTTP反向代理。 推荐通过AWS商城提供的企业版，因为它具有更好的功能，可支持云后台和跨动态主机的缓存清除。

1. 第二个Elastic Load Balancing应用程序负载平衡器在多个可用区的AWS Auto ScalingAdobe商务实例组中分发来自清漆缓存的流量。

1. 在Amazon EC2实例上安装最新版本的Magento Open Source或Adobe商务。 安装由Adobe商务应用程序、Nginx Webserver和PHP组成。 构建Amazon计算机图像(AMI)以在自动缩放组中启动新实例。

1. AmazonElasticsearch服务是用于Adobe商务目录搜索的托管Elasticsearch服务。

1. Amazon ElastiCache for Redis为数据库提供了缓存层。

1. 使用Amazon Aurora或AmazonRDS简化数据库管理(包括高可用性和多主控配置)。

1. EFSMount Target有助于将Amazon弹性文件系统(AmazonEFS)映射到清漆和Adobe商务实例。

1. 使用Amazon EFS跨清漆访问共享配置，并跨Adobe商务实例访问共享媒体资产。

## 云服务

除了提供支持技术平台以在AWS上围绕您的Adobe商务环境启用DevOps流程外，AWS还提供一系列服务，这些服务可以提供（在没有的情况下）或增强您现有的软件配置管理(SCM)解决方案。 这包括AWSCodeCommit、AWSCodeBuild、AWSCodePipeline和AWSCodeDeploy，它们允许进行受管的源代码控制、构建、连续集成/连续部署(CI/CD)和部署服务。

## 云迁移

Adobe商务迁移到AWS的价值主张，因为提供了操作洞察力和敏捷性的多项服务，而得到了进一步的增强。 我们的意思是，对平台的操作分析不仅从技术角度（例如，每小时请求数），还从业务操作角度（例如，每小时订单数），特别是当这两组数据可以结婚时。 这可以近乎实时地了解促销活动效果、平台运营成本以及几乎无限数量的其他指标。

Adobe商务设置到AWS后，可以使用云中提供的完全托管的替代方案替换特定的应用程序依赖项。 例如，许多应用程序的数据库可以轻松替换为Amazon关系数据库服务(AmazonRDS)，而不是直接在EC2实例上托管关系数据库。 此策略的好处是，无差别组件的运营责任可以卸载到AWS，而无需对核心应用程序进行重大更改。

在AWS上运行Adobe商务(Magento Open Source和Adobe商务版本)时，有几个部署选项可用。 最合适的选择取决于贵机构对成本、规模、可用性和灵活性的要求，以及贵机构的AWS和Adobe商务技能。
