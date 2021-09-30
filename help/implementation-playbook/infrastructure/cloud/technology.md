---
title: 云基础架构技术
description: 深入了解我们在云基础架构上用于Adobe商务的技术集合。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# 技术

正如我们前面提到的，Adobe商务利用许多软件解决方案来支持该平台。 具体来说，就生产而言，我们已对云基础架构上的Adobe商务中包含的一些技术解决方案和功能进行了划分，这些解决方案和功能有助于充分利用您的生产环境。

![显示云基础架构技术Adobe商务的图表](../../../assets/playbooks/infrastructure-technology.svg)

## 软件解决方案

- **Nginx** — 使用PHP-FPM的Web服务器。有一个实例具有多个工作程序。

- **GlusterFS** — 文件服务器，用于管理所有静态文件部署和与四个目录装载的同步：
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis** — 每个VM一台服务器，其中只有一台处于活动状态，另两台作为副本。

- **Elasticsearch** — 搜索Adobe商务版本2.2.x及更高版本。

- **Galera** — 数据库群集，每个节点具有一个MariaDB MySQL数据库，每个数据库中的唯一ID自动递增设置为3。

## 功能和优点

- 在VPC中，有三个专用实例，在三个单独的可用区或数据中心之间有一个弹性负载平衡器。

- 针对可能导致单个实例失败的事件提供更高的可复原性。 例如，整个AWS可用区或数据中心发生停机。

- 在不到15分钟的时间内，整个堆栈（包括Web、缓存、搜索和数据库）实现零停机时间扩展。
