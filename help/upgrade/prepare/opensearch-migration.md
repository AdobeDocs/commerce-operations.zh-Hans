---
title: 从Elasticsearch迁移到OpenSearch
description: 了解如何替换用于Adobe Commerce本地安装的搜索引擎。
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 54aef3d7db7b8333721fb56db0ba8f098aea030b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 迁移到OpenSearch

OpenSearch是Elasticsearch 7.10.2的开源分支，在Elasticsearch更改许可后创建。

从2.4.4、2.4.3-p2和2.3.7-p3开始，Adobe Commerce支持OpenSearch。 尽管云基础架构上的Elasticsearch不再支持内部部署，但它仍会持续支持Adobe Commerce。 从版本2.4.6开始，OpenSearch在管理员配置设置中拥有自己的模块和字段。

## 迁移路径

迁移到OpenSearch的步骤非常简单，很大程度上遵循Elasticsearch配置的步骤。 这些步骤假定Adobe Commerce是唯一使用搜索引擎的应用程序。 如果有多个应用程序使用搜索引擎，请遵循官方迁移指南[从开源Elasticsearch迁移到OpenSearch](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/)。

1. 确保您的安装符合[搜索引擎先决条件](../../installation/prerequisites/search-engine/overview.md)。

1. 将站点置于[维护模式](../../installation/tutorials/maintenance-mode.md)。

1. （可选）卸载Elasticsearch。

1. [安装OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/)。

1. [配置搜索引擎](../../configuration/search/configure-search-engine.md)并执行相关任务，如刷新缓存和重新索引目录搜索索引。

无需进一步更改配置值。
