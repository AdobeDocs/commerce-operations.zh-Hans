---
title: 搜索引擎概述
description: Adobe Commerce和Magento Open Source的搜索引擎选项概述。
source-git-commit: 52c472bf80942339b511292243b5da9babf829d9
workflow-type: tm+mt
source-wordcount: '161'
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

[搜索引擎先决条件]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html
[为搜索引擎配置nginx]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html
[为搜索引擎配置Apache]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html
[Elasticsearch]: https://www.elastic.co
[Elasticsearch documentation]: https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html
[安装商务软件]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-install.html
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
