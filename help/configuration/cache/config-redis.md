---
title: 配置Redi
description: 获取Redis功能的概述并启动Redis配置。
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# 配置Redi

Redis功能包括：

- PHP会话存储
- 基于标记的缓存清理，无需 `foreach` 循环
- 磁盘内保存和主控/从复制

## 安装Redis

安装和配置Redis软件不在本指南的涵盖范围内。 咨询资源，例如：

- [“下载密文”页面](https://redis.io/download)
- [雷迪斯快速入门](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [密文文档页面](https://redis.io/docs)

## 设置Redis配置

根据您的安装，您通常可以在以下文件之一中找到Redis配置： `/etc/redis/redis.conf` 或 `/etc/redis/<port>.conf`

为了根据您的要求优化Redis实例，您可以使用每个会话、商务缓存和FPC的专用实例来获得最佳结果。

对于会话，Adobe建议您启用持久性，以使用以下任一持久性选项将Redis数据复制到磁盘：常规Redis数据库备份(RDB)快照或仅附加文件(AOF)持久性日志。

- **Redis数据库备份** (RDB)快照在指定时间后（自上次保存以来发生了最小数量的更改）将完整数据库存储在转储文件中。 使用 `save` 设置 `redis.conf` 文件来配置此设置。

- **仅附加文件** (AOF)将发送给Redis的每个写操作存储在日志文件中。 Redis仅在重新启动时读取此文件，并使用它恢复原始数据集。

您还可以同时启用RDB和AOF选项。 有关包括持久性选项的利弊在内的其他详细信息，请参阅 [Redis持久性文档](https://redis.io/topics/persistence).

对于缓存实例，请设置该实例，使其足够大，可存储整个Commerce缓存。 大小要求取决于不同的因素，如产品数和商店查看次数。 作为起点，您可以使用文件系统上缓存文件夹的大小。 例如，如果 `var/cache` 文件系统上的文件夹为5 GB，请设置至少为5 GB的Redis实例。 缓存实例不需要持久性，因为可以还原商务缓存。 请参阅 [Redis缓存指南](https://redis.io/docs/manual/eviction/).

为了进行性能调整，您还可以启用以下用于异步删除的设置。 这些设置不会更改Redis的行为。 另请参阅 [雷迪新闻](http://antirez.com/news/93) 有关异步删除的详细信息。

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

在Redis 6.x及更高版本上，您还可以添加以下值：

```ini
lazyfree-lazy-user-del yes
```
