---
title: 硬件Recommendations
description: 查看与Adobe Commerce部署和Magento Open Source部署的最佳性能相关的推荐硬件列表。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---


# 硬件建议

## CPU

[!DNL Commerce] web节点提供所有未缓存或无法通过应用程序缓存的请求。 一个CPU核心可以提供大约两个（有时最多四个） [!DNL Commerce] 请求。 使用以下等式确定处理所有传入请求而不将其置于队列中所需的Web节点/核心数量：

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

如果预计商店的负载会发生变化，则可以在活动销售期间手动增加Web节点/核心的数量。 或者，可以使用自动缩放模型来自动扩展Web层。

## 内存

### PHP

Magento的PHP内存要求根据系统的部署方式而有所不同。  通常，如果要设置单个服务器存储，我们建议为2G配置PHP内存。  如果您使用管道部署来设置站点，我们建议在构建服务器上设置2 GB，在Web节点上设置1 GB。

情景和预期PHP内存要求：

* Web节点仅提供店面页面：256 MB
* 具有大目录的Web节点提供管理页面：1 GB
* [!DNL Commerce] 创建具有大目录的站点索引：>256 MB(请参阅 [高级设置](../performance/advanced-setup.md) 以优化性能。)
* [!DNL Commerce] 编译和部署静态资产：756兆字节
* [!DNL Commerce] 性能工具包配置文件生成：>1 GB PHP RAM，>16 MB [!DNL MySQL] TMP_TABLE_SIZE和MAX_HEAP_TABLE_SIZE设置

### [!DNL MySQL]

的 [!DNL Commerce] 数据库（以及任何其他数据库）对可用于存储数据和索引的内存量非常敏感。 有效利用 [!DNL MySQL] 数据索引，可用内存量至少应接近数据库中存储数据大小的一半。

### 缓存

如果要部署多个 [!DNL Commerce] 和使用Redis或 [!DNL Varnish] 对于您的缓存，请牢记以下原则：

* [!DNL Varnish] 全页缓存内存失效有效，建议分配足够的内存 [!DNL Varnish] 保存您记忆中最受欢迎的页面
* 会话缓存是为Redis的单独实例配置的一个好候选项。  此缓存类型的内存配置应考虑网站的购物车放弃策略以及会话在缓存中应保持多长时间
* Redis应该有足够的内存来存储内存中的所有其他缓存，以获得最佳性能。  块缓存将是确定要配置的内存量的关键因素。  块缓存会相对于网站上的页面数量（SKU x存储查看次数）增长

## 网络带宽

足够的网络带宽是Web节点、数据库、缓存/会话服务器和其他服务之间数据交换的关键要求之一。 因为 [!DNL Commerce] 有效地利用缓存实现高性能，您的系统可以主动与Redis等缓存服务器交换数据。 如果Redis位于远程服务器上，则必须在Web节点和缓存服务器之间提供足够的网络通道，以防止读/写操作出现瓶颈。
