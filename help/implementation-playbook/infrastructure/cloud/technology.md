---
title: 云基础架构技术
description: 深入了解我们在云基础架构上用于Adobe Commerce的技术集合。
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 技术

正如我们前面提到的，Adobe Commerce利用许多软件解决方案来支持该平台。 具体来说，就生产而言，我们已对云基础架构上的Adobe Commerce中包含的一些技术解决方案和功能进行了划分，这些解决方案和功能有助于充分利用您的生产环境。

![显示Adobe Commerce云基础架构技术的图表](../../../assets/playbooks/infrastructure-technology.svg)

## 软件解决方案

- **Nginx** — 使用PHP-FPM的Web服务器。 有一个实例具有多个工作程序。

- **GlusterFS** — 用于管理所有静态文件部署和与四个目录装载的同步的文件服务器：
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **雷迪斯** — 每个VM一台服务器，其中只有一个活动服务器，另外两台作为副本。

- **Elasticsearch** — 搜索Adobe Commerce版本2.2.x及更高版本。

- **加莱拉** — 数据库群集，每个节点具有一个MariaDB MySQL数据库，每个数据库中的唯一ID自动递增设置为3。

## 功能和优点

- 在VPC中，有三个专用实例，在三个单独的可用区或数据中心之间有一个弹性负载平衡器。

- 针对可能导致单个实例失败的事件提供更高的可复原性。 例如，整个AWS可用区或数据中心发生停机。

- 在不到15分钟的时间内，在整个堆栈（包括Web、缓存、搜索和数据库）中实现零停机时间扩展。
