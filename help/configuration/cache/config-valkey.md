---
title: 配置Valkey
description: 大致了解Valkey功能并启动Valkey配置。
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: b2cf71bfda3e5db8e27eb28d764cf99216454e33
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# 配置Valkey

Valkey功能包括：

- PHP会话存储
- 无`foreach`循环的基于标记的缓存清理
- 磁盘上保存和主/从复制

## 安装Valkey

要安装和配置Valkey软件，请查阅以下资源：

- [下载Valkey页](https://valkey.io/download/)
- [Valkey快速入门](https://valkey.io/topics/quickstart/)
- [Valkey文档页](https://valkey.io/docs)

## 设置Valkey配置

根据您的安装，您通常可以在`/etc/valkey/valkey.conf`文件或`/etc/valkey/<port>.conf`文件中找到Valkey配置。

为了根据您的要求优化Valkey实例，您可以为每个会话、Commerce缓存和FPC使用专用实例以获得最佳结果。

Adobe建议为会话启用持久性以将Valkey数据复制到磁盘。 可以使用Valkey数据库备份(RDB)快照或仅附加文件(AOF)持久性日志。

- **RDB** （Valkey数据库）快照在给定时间后将完整数据库存储在转储文件中，该时间自上次保存以来已更改最小数量的键。 使用`save`文件中的`valkey.conf`设置配置此设置。

- **仅附加文件** (AOF)将发送到Valkey的每个写入操作存储在日志文件中。 Valkey仅在重新启动时读取此文件，并使用它恢复原始数据集。

您还可以同时启用RDB和AOF选项。 有关包括持久性选项的优缺点的其他详细信息，请参阅[Valkey持久性文档](https://valkey.io/topics/persistence/)。

对于缓存实例，请设置该实例，使其足够大，用于存储整个Commerce缓存。 大小要求取决于不同的因素，如产品数量和商店查看次数。 作为起点，您可以使用文件系统中缓存文件夹的大小。 例如，如果文件系统上的`var/cache`文件夹为5 GB，请将Valkey实例设置为至少5 GB以启动。 缓存实例不需要持久性，因为可以恢复Commerce缓存。

对于性能优化，可以为异步删除启用以下设置。 这些设置不会更改Valkey的行为。

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
