---
title: 配置Redis
description: 了解如何配置Redis缓存以优化Adobe Commerce性能。 了解功能、设置步骤和配置最佳实践。
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# 配置Redis

Redis功能包括：

- PHP会话存储
- 无`foreach`循环的基于标记的缓存清理
- 磁盘上保存和主/从复制

## 安装Redis

安装和配置Redis软件超出了本指南的范围。 查阅资源，例如：

- [下载Redis页面](https://redis.io/download)
- [Redis快速入门](https://redis.io/docs/latest/)
- [数字海洋](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis文档页面](https://redis.io/docs)

## 设置Redis配置

根据您的安装，您通常可以在以下文件中找到Redis配置： `/etc/redis/redis.conf`或`/etc/redis/<port>.conf`

为了根据您的要求优化Redis实例，您可以为每个会话使用一个专用实例、Commerce缓存和FPC，以获得最佳结果。

对于会话，Adobe建议启用持久性以使用以下任一持久性选项将Redis数据复制到磁盘：常规Redis数据库备份(RDB)快照或仅附加文件(AOF)持久性日志。

- **Redis Database Backup** (RDB)快照在给定时间后将完整数据库存储在转储文件中，该时间自上次保存以来已更改最小密钥数。 使用`save`文件中的`redis.conf`设置配置此设置。

- **仅附加文件** (AOF)将发送到Redis的每个写入操作存储在日志文件中。 Redis仅在重新启动时读取此文件，并使用它恢复原始数据集。

您还可以同时启用RDB和AOF选项。 有关包括持久性选项的优缺点的其他详细信息，请参阅[Redis持久性文档](https://redis.io/topics/persistence)。

对于缓存实例，请设置该实例，使其足够大，用于存储整个Commerce缓存。 大小要求取决于不同的因素，如产品数量和商店查看次数。 作为起点，您可以使用文件系统中缓存文件夹的大小。 例如，如果文件系统上的`var/cache`文件夹为5 GB，请将Redis实例设置为至少5 GB以启动。 缓存实例不需要持久性，因为可以恢复Commerce缓存。 请参阅[Redis缓存指南](https://redis.io/docs/latest/develop/use/)。

对于性能优化，可以为异步删除启用以下设置。 这些设置不会更改Redis的行为。

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
