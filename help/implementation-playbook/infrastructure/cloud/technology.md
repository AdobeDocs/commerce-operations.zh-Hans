---
title: 云基础架构技术
description: 更详细地了解我们在云基础架构上用于Adobe Commerce的技术集合。
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# 技术

如前所述，Adobe Commerce利用许多软件解决方案来支持该平台。 具体而言，在与生产相关的方面，我们细分了Adobe Commerce on cloud infrastructure中包含的一些技术解决方案和功能，它们有助于充分利用您的生产环境。

![显示Adobe Commerce on cloud infrastructure技术的图表](../../../assets/playbooks/infrastructure-technology.svg)

## 软件解决方案

- **恩金克斯** — 使用PHP-FPM的Web服务器。 有一个实例具有多个工作程序。

- **GlusterFS** — 用于管理所有静态文件部署和使用四个目录装载进行同步的文件服务器：
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis** — 每个虚拟机一台服务器，仅一台处于活动状态，另外两台作为复制副本。

- **Elasticsearch** — 搜索Adobe Commerce版本2.2.x及更高版本。

- **OpenSearch** — 搜索Adobe Commerce版本2.4.6及更高版本。

- **加莱拉** — 数据库群集，每个节点有一个MariaDB MySQL数据库，每个数据库的唯一ID的自动增量设置为3。

## 功能和优点

- 在VPC中有三个专用实例，在三个独立的可用区或数据中心之间有一个弹性负载平衡器。

- 对于可能导致单个实例失败的事件，提供了更高的恢复能力。 例如，整个AWS可用区或数据中心的中断。

- 在少于15分钟的时间内跨整个栈栈（包括Web 、缓存、搜索和数据库）进行零停机时间扩展。
