---
title: 从Elasticsearch迁移到OpenSearch
description: 了解如何更换用于Adobe Commerce和Magento Open Source本地安装的搜索引擎。
source-git-commit: 8007ff2e77689ec2058a326924dc34b8d91ee570
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# 迁移到OpenSearch

OpenSearch是在Elasticsearch的许可更改后创建的Elasticsearch7.10.2的开源分支。

自2.4.4、2.4.3-p2和2.3.7-p3起，Adobe Commerce和Magento Open Source支持OpenSearch。 内部部署安装将继续支持Elasticsearch，但云基础架构上的Adobe Commerce不再支持本地安装。

## 迁移路径

迁移到OpenSearch的步骤很简单，基本上遵循Elasticsearch配置的步骤。 这些步骤假定Adobe Commerce是唯一使用搜索引擎的应用程序。 如果多个应用程序使用搜索引擎，请遵循官方迁移指南 [从开源Elasticsearch移动到OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. 确保安装符合 [搜索引擎先决条件](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html).

1. 将网站放置到 [维护模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. （可选）卸载Elasticsearch。

1. [安装OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [配置搜索引擎](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) 并执行相关任务，例如刷新缓存和重新索引目录搜索索引。

无需进一步更改配置值。
