---
title: 配置Redis
description: 大致了解Redis功能并启动Redis配置。
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# 配置Redis

Redis功能包括：

- PHP会话存储
- 基于标记的缓存清理，不使用 `foreach` 循环
- 磁盘上存储和主控/从属复制

## 安装Redis

安装和配置Redis软件超出了本指南的范围。 请参阅以下资源：

- [下载Redis页面](https://redis.io/download)
- [Redis快速入门](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis文档页面](https://redis.io/docs)

## 设置Redis配置

根据您的安装，通常可以在以下文件之一中找到Redis配置： `/etc/redis/redis.conf` 或 `/etc/redis/<port>.conf`

为了根据您的要求优化Redis实例，您可以为每个会话、Commerce缓存和FPC使用专用实例来获取最佳结果。

对于会话，Adobe建议使用以下任一持久性选项启用持久性以将Redis数据复制到磁盘：常规Redis数据库备份(RDB)快照或仅附加文件(AOF)持久性日志。

- **Redis数据库备份** (RDB)快照在给定时间后将完整数据库存储在转储文件中，此时自上次保存以来已更改最小密钥数。 使用 `save` 在中设置 `redis.conf` 文件，以配置此设置。

- **仅附加文件** (AOF)将发送到Redis的每个写入操作存储在日志文件中。 Redis仅在重新启动时读取此文件，并使用它恢复原始数据集。

您还可以同时启用RDB和AOF选项。 有关包括持久性选项的优缺点在内的更多详细信息，请参阅 [Redis持久性文档](https://redis.io/topics/persistence).

对于缓存实例，请设置该实例，使其足够大以存储整个Commerce缓存。 大小要求取决于不同的因素，如产品数量和商店查看次数。 首先，您可以使用文件系统中缓存文件夹的大小。 例如，如果 `var/cache` 文件系统中的文件夹为5 GB，请将您的Redis实例设置为至少5 GB以开始。 缓存实例不需要持久性，因为可以恢复Commerce缓存。 参见 [Redis缓存指南](https://redis.io/docs/manual/eviction/).

对于性能优化，您可以启用以下异步删除设置。 这些设置不会更改Redis的行为。

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
