---
title: 搜索引擎概述
description: 了解Elasticsearch和OpenSearch for Adobe Commerce目录搜索、先决条件、Web服务器设置和安装后维护任务。
feature: Configuration, Search
exl-id: 0ea78ca2-0bca-4d61-980a-02fb7da04553
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%
---
# 搜索引擎概述

从版本2.4.4开始，Adobe Commerce要求[Elasticsearch](https://www.elastic.co)或[OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/)作为目录搜索引擎。 2.4.x的先前版本要求使用Elasticsearch。 有关安装搜索引擎和初始配置的详细信息，请参阅以下主题：

- [搜索引擎先决条件](../../installation/prerequisites/search-engine/overview.md)
- [为搜索引擎配置nginx](../../installation/prerequisites/search-engine/configure-nginx.md)
- [为搜索引擎配置Apache](../../installation/prerequisites/search-engine/configure-apache.md)
- [安装Commerce软件](../../installation/composer.md) （命令行界面）

安装搜索引擎并与Adobe Commerce集成后，必须执行其他维护：

- [配置搜索停用词](search-stopwords.md)
- [搜索引擎配置](configure-search-engine.md)

