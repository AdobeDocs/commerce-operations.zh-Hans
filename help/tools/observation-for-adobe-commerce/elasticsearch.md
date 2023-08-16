---
title: 此 [!UICONTROL Elasticsearch] 选项卡
description: 了解 [!UICONTROL Elasticsearch] 选项卡/ [!DNL Observation for Adobe Commerce].
exl-id: e98d351d-b3b1-47bc-bc0d-f96ba9ec2b80
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# 此 [!UICONTROL Elasticsearch] 选项卡

## [!UICONTROL Cluster Status Summary]:

![群集状态摘要](../../assets/tools/cluster-status-summary.jpg)

在选定的时间范围内， **[!UICONTROL Cluster Status Summary]** 框架显示 [!DNL Elasticsearch] 群集已通过。 在此示例中，在选定的时间范围内，集群在选定的时间范围内分别处于绿色和黄色状态一次。

## [!UICONTROL Active Primary Shards]

![活动主分片](../../assets/tools/active-primary-shards.jpg)

此 **[!UICONTROL Active Primary Shards]** 根据所选帐户的活动主分片的数量，框架将显示不同的数字 [!DNL Elasticsearch] 服务。

从 [!DNL Elasticsearch]：最终指南 [2.x]：

“在 [可动态更新的索引](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html)，我们解释说碎片是一个Lucene索引，并且 [!DNL Elasticsearch] 索引是分片的集合。 您的应用程序与索引对话，并且 [!DNL Elasticsearch] 将您的请求路由到相应的分片。 分片是比例单位。 您可以拥有的最小索引是具有单个分片的索引。 这或许足以满足您的需求 — 单个碎片可以保存大量数据 — 但这限制了您的扩展能力。”

创建索引时，将使用该索引创建多个分片。 默认情况下，每个新索引分配五个主分片，这意味着一个索引可以分布到五个节点（每个节点一个分片）。 还有复制分片。 这些主要用于故障转移。 副本分区可以为读取请求提供服务。

## [!UICONTROL Active Shards in Cluster]

![群集中的活动分片](../../assets/tools/active-shards-in-cluster.jpg)

此 **[!UICONTROL Active Shards in Cluster]** 帧显示a中的主分片和副本分片的总数 [!DNL Elasticsearch] 群集。

## [!UICONTROL Index health - this will show the index name and color status]

![索引运行状况](../../assets/tools/index-health.jpg)

此框架显示索引名称和索引颜色状态计数。 向下滚动表，您会看到相同的索引名称，其颜色状态为黄色和红色。 27索引名称后面的数字是状态颜色的计数。 如果为0，则在所选时间范围内没有索引实例处于该颜色状态。

## [!UICONTROL Elasticsearch Status by node information]

![Elasticsearch状态](../../assets/tools/elasticsearch-status-by-node.jpg)

此 **[!UICONTROL Elasticsearch Status by node information]** 框架显示 [!DNL Elasticsearch] 按颜色和节点划分的群集状态。 这有助于指示 [!DNL Elasticsearch] 群集在选定的时间范围内返回什么状态。

## [!UICONTROL Elasticsearch index information]

![索引信息Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

此 **[!UICONTROL Elasticsearch index information]** 该表显示索引名称、它所在的节点、已编制索引的文档数、索引运行状况以及在特定时间的索引大小（以MB为单位）。

## [!UICONTROL Elasticsearch process CPU %]

![Elasticsearch进程CPU](../../assets/tools/elasticsearch-process-cpu.jpg)

此 **[!UICONTROL Elasticsearch process CPU %]** 框架显示进程CPU百分比，方法为 [!DNL Elasticsearch] 在选定的时间范围内处理。

## [!UICONTROL Elasticsearch Memory garbage collection]

![Elasticsearch内存垃圾](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] 是一个Java进程。 如果它在分配的内存上运行不足，它将启动垃圾回收以释放内存。 如果频繁进行垃圾回收，则表明分配的内存可能索引或碎片过多。 也许有机会清理指数和碎片或 [!DNL Elasticsearch] 可能需要更多内存。

## [!UICONTROL Elasticsearch Index information]

![Elasticsearch索引信息](../../assets/tools/elasticsearch-index-information-2.jpg)

创建和更新索引时，索引运行状况可能会发生更改。

## [!UICONTROL Elasticsearch Index Size]

![Elasticsearch索引大小](../../assets/tools/elasticsearch-index-size.jpg)

此 **[!UICONTROL Elasticsearch Index Size]** frame指示所选时间范围内的索引名称和大小。 它可能会指示网站索引方式的问题。

## [!UICONTROL Elasticsearch Errors]

![Elasticsearch错误](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

此 **[!UICONTROL Elasticsearch Errors]** 框架显示错误 [!DNL Elasticsearch] 当所有分片都失败时、搜索存在参数问题、版本错误时，以及所有节点都不可用时，就像空间不足、从黄色状态切换到红色状态一样。

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Elasticsearch未分配分片](../../assets/tools/elasticsearch-unassigned-shards.jpg)

未分配的分片将导致群集从绿色状态移动到黄色状态。
