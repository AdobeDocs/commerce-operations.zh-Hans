---
title: 搜索引擎概述
description: Adobe Commerce和Magento Open Source的搜索引擎选项概述。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# 搜索引擎概述

自版本2.4.4起，Adobe Commerce和Magento Open Source需要 [Elasticsearch] 或 [OpenSearch] 作为目录搜索引擎。 2.4.x的先前版本需要Elasticsearch。 有关安装搜索引擎和初始配置的详细信息，请参阅以下主题：

- [搜索引擎先决条件]
- [为搜索引擎配置nginx]
- [为搜索引擎配置Apache]
- [安装商务软件] （命令行界面）

安装搜索引擎并将其与Adobe Commerce集成后，必须执行其他维护：

- [配置搜索秒词](search-stopwords.md)
- [搜索引擎配置](configure-search-engine.md)

<!-- Link Definitions -->

[搜索引擎先决条件]: ../../installation/prerequisites/search-engine/overview.md
[为搜索引擎配置nginx]: ../../installation/prerequisites/search-engine/configure-nginx.md
[为搜索引擎配置Apache]: ../../installation/prerequisites/search-engine/configure-apache.md
[Elasticsearch]: https://www.elastic.co
[安装商务软件]: ../../installation/composer.md
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
