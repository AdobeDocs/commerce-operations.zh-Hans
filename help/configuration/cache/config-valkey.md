---
title: 安装和设置Valkey
description: 了解如何使用Adobe Commerce安装和配置Valkey以进行缓存和会话存储。 发现优化和性能调整的选项。
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
TQID: 'https://experienceleague.adobe.com/Ef4WREy0eq0ChsrI5-0FtrjMZWNjwr7l71Pm-RHD1GI'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 414
ht-degree: 0%

---

# 安装和设置Valkey

Valkey是一个开源、与Redis兼容的内存中数据存储，可用作缓存后端和会话存储。 主要功能包括：

- PHP会话存储
- 无`foreach`循环的基于标记的缓存清理
- 磁盘上保存和主/从复制

{{cloud-cache-config}}

## 安装Valkey

要安装和配置Valkey软件，请查阅以下资源：

- [下载Valkey页面](https://valkey.io/download/){target="_blank"}
- [Valkey快速入门](https://valkey.io/topics/quickstart/){target="_blank"}
- [Valkey文档页面](https://valkey.io/docs){target="_blank"}

## 设置Valkey配置

根据您的安装，您通常可以在`/etc/valkey/valkey.conf`文件或`/etc/valkey/<port>.conf`文件中找到Valkey配置。

为了根据您的要求优化Valkey实例，您可以为每个会话、Commerce缓存和FPC使用专用实例以获得最佳结果。

Adobe建议为会话启用持久性以将Valkey数据复制到磁盘。 可以使用Valkey数据库备份(RDB)快照或仅附加文件(AOF)持久性日志。

- **RDB** （Valkey数据库）快照在给定时间后将完整数据库存储在转储文件中，该时间自上次保存以来已更改最小数量的键。 使用`valkey.conf`文件中的`save`设置配置此设置。

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
