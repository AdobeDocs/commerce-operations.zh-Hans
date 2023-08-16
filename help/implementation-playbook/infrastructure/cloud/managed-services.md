---
title: Managed Services
description: 查看Managed Services、客户和云服务提供商在云基础架构实施方面为您的Adobe CommerceAdobe的责任。
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
feature: Cloud, Services
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Managed services

默认情况下，云基础架构托管服务上的Adobe Commerce是安全的。

![显示Adobe Commerce Managed Services的图表](../../../assets/playbooks/managed-services.svg)

## 分担责任

Adobe Commerce Pro计划依赖于共同责任安全模式。 在此模型中，不同方面负责维护系统的安全。 这种方法既允许灵活，又允许使用同类最佳的云技术。

![显示Adobe Commerce共享责任模型的图](../../../assets/playbooks/shared-responsibility.svg)

### AdobeManaged Services职责

Managed ServicesAdobe负责Adobe Commerce Pro云环境、核心Adobe Commerce Pro应用程序代码和内部商务系统的安全性和可用性。 这包括但不限于：

- 服务器级修补
- 运行必要的服务以提供Adobe Commerce Pro计划
- 漏洞测试
- 安全事件日志记录和监控
- 事件管理
- 运行监控
- 全天候支持
- 确保客户基础架构按照SLA提供

AdobeManaged Services还负责管理服务器防火墙配置(iptables)和外围防火墙配置（安全组）。 Adobe还可以定期向核心应用程序发布安全更新。 客户有责任应用这些修补程序。 这些领域都包含在云基础架构系统上的Adobe Commerce PCI认证中。

### AWS职责

AdobeManaged Services使用Amazon Web Services (AWS)进行云服务器基础架构。 AWS负责网络安全，包括通过防火墙系统和入侵检测系统(IDS)进行路由、交换和外围网络安全。 AWS负责管理Adobe Commerce云环境的数据中心的物理安全，以及环境安全，以确保实现正确的电源、冷却和机制控制。

Adobe Commerce Pro计划使用：

- Amazon弹性计算云(EC2)
- Amazon Simple Storage Service (S3)
- Amazon弹性块存储(EBS)
- Amazon Virtual Private Cloud (VPC)
- Amazon弹性负载平衡器(ELB)
- Amazon Cloud Trail服务。

Amazon拥有广泛的合规计划，其中包括PCI DSS、SOC 2和ISO 27001认证。

### 解决方案合作伙伴/客户责任

客户主要负责在Adobe Commerce Pro计划云环境中运行的Adobe Commerce应用程序的自定义实施的安全性。 这包括：

- 确保应用程序和安全监控活动的安全配置和编码，包括渗透测试和定期漏洞扫描。

- 在其系统中使用的任何自定义、扩展、其他应用程序或集成的安全性。

- 用户的安全性以及对其配置和应用程序的访问权限的授予。

- 客户可控制其非生产环境的所有代码部署。 此控制还负责将应用程序安全修补程序应用到核心Adobe Commerce应用程序、扩展或任何自定义代码。

- 客户应对其定制应用程序执行渗透测试。 客户、实施合作伙伴或Adobe Commerce专业服务人员可以通过技术资源来履行这些职责。

- 客户负责其定制应用程序和自己的流程的PCI要求。 客户的PCI合规性建立在AWS和Adobe Commerce的PCI认证之上，以尽量减少必须审查的方面。
