---
title: “ [!UICONTROL Elasticsearch] 选项卡”
description: 了解 [!UICONTROL Elasticsearch] 选项卡 [!DNL Observation for Adobe Commerce].
source-git-commit: 2427a18ea67833bc50912ef78be29d4320b5b205
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---


# 的 [!UICONTROL Elasticsearch] 选项卡

## [!UICONTROL Cluster Status Summary]:

![群集状态摘要](../../assets/tools/cluster-status-summary.jpg)

在选定的时间范围内， **[!UICONTROL Cluster Status Summary]** 框架显示 [!DNL Elasticsearch] 群集已通过。 在此示例中，在选定的时间范围内，群集在选定时间范围内处于“绿色”状态一次，在“黄色”状态下一次。

## [!UICONTROL Active Primary Shards]

![活动主碎片](../../assets/tools/active-primary-shards.jpg)

的 **[!UICONTROL Active Primary Shards]** 框架将根据所选帐户的活动主共享数量显示不同的数量 [!DNL Elasticsearch] 服务。

从 [!DNL Elasticsearch]:最终指南 [2.x]:

“在 [可动态更新的索引](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html)，我们解释说，碎片是卢塞内指数，而且 [!DNL Elasticsearch] index是碎片的集合。 您的应用程序会与索引进行对话，并且 [!DNL Elasticsearch] 将请求路由到相应的碎片。 碎片是比例单位。 您可以拥有的最小索引是包含单个分片的索引。 这可能足以满足您的需求 — 单个分片可以保存大量数据 — 但它限制了您扩展的能力。”

创建索引后，会使用该索引创建多个分片。 默认情况下，每个新索引将分配五个主要分片，这意味着一个索引可以跨五个节点分布（每个节点一个分片）。 还有复制品碎片。 这些主要用于故障转移。 副本碎片可以提供读取请求。

## [!UICONTROL Active Shards in Cluster]

![群集中的活动碎片](../../assets/tools/active-shards-in-cluster.jpg)

**[!UICONTROL Active Shards in Cluster]** - [!DNL Elasticsearch] 群集。

## [!UICONTROL Index health - this will show the index name and color status]

![指数运行状况](../../assets/tools/index-health.jpg)

此帧将显示索引名称和索引颜色状态计数。 向下滚动表格时，将看到具有相同的索引名称，其状态为“黄色”和“红色”。 在27个索引名称后面显示的编号是状态颜色的计数。 如果为零，则在这些选定时间范围内没有索引处于该颜色状态的实例。

## [!UICONTROL Elasticsearch Status by node information]

![Elasticsearch状态](../../assets/tools/elasticsearch-status-by-node.jpg)

的 **[!UICONTROL Elasticsearch Status by node information]** 框架显示 [!DNL Elasticsearch] 按颜色、按节点划分的群集状态。 这将有助于指示 [!DNL Elasticsearch] 群集在选定的时间范围内返回什么状态。

## [!UICONTROL Elasticsearch index information]

![Elasticsearch索引信息](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

此 **[!UICONTROL Elasticsearch index information]** 表显示索引名称、其所在节点、已索引文档的数量、索引运行状况，以及特定时间的索引大小（以MB为单位）。

## [!UICONTROL Elasticsearch process CPU %]

![Elasticsearch进程CPU](../../assets/tools/elasticsearch-process-cpu.jpg)

的 **[!UICONTROL Elasticsearch process CPU %]** 帧显示进程CPU%，按 [!DNL Elasticsearch] 处理时间范围。

## [!UICONTROL Elasticsearch Memory garbage collection]

![Elasticsearch内存垃圾](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] 是一个Java进程。 如果它在已分配的内存上运行低，则它将启动垃圾收集以释放内存。 如果垃圾收集频繁，则表示已分配内存可能存在过多的索引或碎片。 或许有机会清理指数和碎片，或 [!DNL Elasticsearch] 可能需要更多内存。

## [!UICONTROL Elasticsearch Index information]

![Elasticsearch索引信息](../../assets/tools/elasticsearch-index-information-2.jpg)

创建和更新索引后，索引运行状况可能会发生更改。

## [!UICONTROL Elasticsearch Index Size]

![Elasticsearch索引大小](../../assets/tools/elasticsearch-index-size.jpg)

的 **[!UICONTROL Elasticsearch Index Size]** frame表示选定时间范围内的索引名称和大小。 它可能表示网站的索引方式存在问题。

## [!UICONTROL Elasticsearch Errors]

![Elasticsearch错误](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

的 **[!UICONTROL Elasticsearch Errors]** 帧将显示错误， [!DNL Elasticsearch] 与空间不足一样，当所有分片都失败时、当搜索存在参数问题时、版本错误时以及当所有节点都不可用时，从“黄色”状态切换为“红色”状态。

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Elasticsearch未分配分片](../../assets/tools/elasticsearch-unassigned-shards.jpg)

未分配的分片将导致群集从绿色状态变为黄色状态。
