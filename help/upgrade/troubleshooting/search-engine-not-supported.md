---
title: 当前搜索引擎不受支持
description: 遇到有关不受支持的Magento Open Source引擎的错误后，对您的Adobe Commerce或搜索引擎升级进行故障排除。
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# 当前搜索引擎不受支持

以下错误消息指示您从中升级的Adobe Commerce或Magento Open Source版本配置为使用您升级到的版本不支持的目录搜索引擎：

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

此错误表示以下条件之一在Adobe Commerce或Magento Open Source的较低级别版本上为true：

- 搜索引擎设置为MySQL。
- 搜索引擎设置为不再支持的Elasticsearch版本。

使用以下命令检查当前搜索引擎：

```bash
bin/magento config:show catalog/search/engine
```

如果返回值为 `mysql`， `elasticsearch`，或 `elasticsearch6`.

>[!WARNING]
>
>如果您收到此错误，则表明您的安装处于不一致状态，并且无法访问管理员。 我们建议您在解决此错误时还原到之前的版本。 为此，请运行以下命令之一：
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>位置 `<version>` 是您运行的Magento的版本 **早于** 升级。 例如， `2.3.5`.

按照以下各节中所述的准则从不一致状态中恢复。

## 如果您的搜索引擎为 `mysql`

在2.4之前，MySQL是默认的目录搜索引擎，但不再支持MySQL这种功能。 现在，在升级到2.4之前，您必须安装和配置Elasticsearch或OpenSearch作为搜索引擎。

使用以下资源可以帮助您完成此过程：

- [安装和配置搜索引擎](../../configuration/search/overview-search.md)
- [搜索引擎配置](../../configuration/search/configure-search-engine.md)

配置搜索引擎并重新索引后，即可升级到2.4。

## 如果您的搜索引擎为 `elasticsearch`

不再支持Elasticsearch6及更早版本。

值 `elasticsearch` 指示您的Adobe Commerce或Magento Open Source低级版本配置为使用Elasticsearch2.x。不再支持此版本的Elasticsearch。

升级到2.4之前必须执行以下任务：

1. 更新到Commerce支持的Elasticsearch版本。 请参阅 [升级Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有关备份数据、检测潜在的迁移问题以及测试升级以便部署到生产环境之前的完整说明。 根据您当前版本的Elasticsearch，可能需要也可能不需要完全重新启动群集。

   >[!NOTE]
   >
   >Elasticsearch需要JDK 1.8或更高版本。 参见 [安装Java软件开发工具包(JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 以检查已安装的JDK版本。

1. [配置Elasticsearch](../../configuration/search/configure-search-engine.md) 并重新索引。

配置搜索引擎并重新索引后，即可升级到2.4。
