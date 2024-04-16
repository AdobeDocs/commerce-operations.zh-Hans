---
title: 硬件Recommendations
description: 查看与Adobe Commerce部署的最佳性能相关的推荐硬件列表。
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# 硬件建议

## CPU

[!DNL Commerce] Web节点提供未缓存或无法通过应用程序缓存的所有请求。 一个CPU核心最多可以处理两个（有时最多四个） [!DNL Commerce] 请求有效。 使用以下公式可确定需要有多少Web节点/核心来处理所有传入请求，而无需将它们排入队列：

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

如果您预计商店的负载会发生变化，则可以手动增加活跃销售期间的Web节点/核心数量。 或者，可以使用自动缩放模型来自动扩展Web层。

## 内存

### PHP

根据Magento的部署方式，系统有不同的PHP内存要求。  通常，如果要设置单个服务器存储，我们建议为2G配置PHP内存。  如果您使用管道部署设置站点，我们建议在构建服务器上使用2 GB，在Web节点上使用1 GB。

方案和预期的PHP内存要求：

* 仅提供店面页面的Web节点：256 MB
* Web节点使用大型目录为管理员页面提供服务：1 GB
* [!DNL Commerce] cron使用大型目录索引网站：>256 MB(请参阅 [高级设置](../performance/advanced-setup.md) 以优化性能。)
* [!DNL Commerce] 编译和部署静态资产：756 MB
* [!DNL Commerce] 性能工具包配置文件生成：大于1 GB PHP RAM，大于16 MB [!DNL MySQL] TMP_TABLE_SIZE和MAX_HEAP_TABLE_SIZE设置

### [!DNL MySQL]

此 [!DNL Commerce] 数据库（以及任何其他数据库）对可用于存储数据和索引的内存量敏感。 有效利用 [!DNL MySQL] 数据索引，可用的内存量至少应接近数据库中存储的数据大小的一半。

### 缓存

如果要部署多个 [!DNL Commerce] 使用Redis或 [!DNL Varnish] 对于您的缓存，请牢记以下原则：

* [!DNL Varnish] 全页缓存内存失效有效，建议分配足够的内存给 [!DNL Varnish] 将你最受欢迎的分页保存在记忆中
* 会话缓存是为Redis的单独实例配置的良好候选项。  此缓存类型的内存配置应考虑站点的购物车放弃策略以及会话预计在缓存中保留的时长
* Redis应分配足够的内存来保存内存中的所有其他缓存，以获得最佳性能。  块缓存将是决定要配置的内存量的关键因素。  块缓存会相对于网站上的页面数量而增长（sku数量x存储查看数量）

## 网络带宽

充足的网络带宽是Web节点、数据库、缓存/会话服务器和其他服务之间数据交换的关键要求之一。 因为 [!DNL Commerce] 有效地利用缓存实现高性能，您的系统可以主动与Redis等缓存服务器交换数据。 如果Redis位于远程服务器上，则必须在Web节点和缓存服务器之间提供充足的网络通道，以防止读/写操作出现瓶颈。
