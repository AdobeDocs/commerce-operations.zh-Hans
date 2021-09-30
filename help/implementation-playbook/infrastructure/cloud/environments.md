---
title: 云基础架构环境
description: 为正确的用例使用正确的环境。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# 环境

Adobe云基础架构上的商务Pro架构支持可用于开发、测试和启动您的商店的环境。 每个环境都包含一个数据库和一个Web服务器。 Adobe商务利用的四个环境包括：

- **集成** — 提供单个环境分支，您最多可以创建四个其他环境分支。这允许最多五个活动分支部署到“平台即服务”(PaaS)容器。

- **暂存** — 提供一个部署到专用“基础架构即服务”(IaaS)容器的单个环境分支。

- **生产** — 提供一个部署到专用“基础架构即服务”(IaaS)容器的单个环境分支。

- **全局主控** — 提供一个部署到“平台即服务”(PaaS)容器的主控分支。

![显示Adobe商务云环境之间关系的图表](../../../assets/playbooks/environment-diagram.svg)

## Git分支

集成环境提供了一个基本集成分支，其中包含部署到Platform-as-a-Service(PaaS)容器的Adobe商务代码。

云基础架构环境上的Adobe商务支持灵活、连续的集成流程。 首先，将集成分支克隆到本地项目文件夹。 创建新分支或多个分支，以开发新功能、配置更改和添加扩展。 借助开发的代码分支和相应的配置文件，您的代码更改可以合并到集成分支，以便进行更全面的测试。

![显示用于Adobe商务云环境的基于git的分支策略的图表](../../../assets/playbooks/branching-diagram.svg)
