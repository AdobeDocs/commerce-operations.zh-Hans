---
title: 不支持当前搜索引擎
description: 在遇到有关不支持的搜索引擎的错误后，对Adobe Commerce或Magento Open Source升级进行故障诊断。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---


# 不支持当前搜索引擎

以下错误消息表示您从升级的Magento版本配置为使用在您升级到的Magento版本中不受支持的目录搜索引擎：

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

此错误表示以下任一条件在Adobe Commerce或Magento Open Source的下级版本中为true:

- 搜索引擎设置为MySQL。
- 搜索引擎已设置为不再支持的Elasticsearch版本。

使用以下命令检查当前搜索引擎：

```bash
bin/magento config:show catalog/search/engine
```

如果返回的值为 `mysql` 或 `elasticsearch`.

>[!WARNING]
>
>如果您收到此错误，则Magento状态不一致，您无法访问管理员。 我们建议您在解决此错误时还原到之前的版本。 要执行此操作，请运行以下命令之一：
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
>其中 `<version>` 是您运行的Magento版本 **之前** 升级。 例如， `2.3.5`.

请遵循以下各节中所述的准则，从不一致的状态中恢复。

## 如果您的搜索引擎为 `mysql`

在2.4之前， MySQL是默认的目录搜索引擎，但MySQL不再支持此容量。 现在，您必须先安装并配置Elasticsearch作为搜索引擎，然后才能升级到2.4。

使用以下资源帮助您完成此过程：

- [安装和配置Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)
- [安装Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- 配置Elasticsearch以使用 [nginx](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-nginx.html) 或 [Apache](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-apache.html)
- [配置Magento以使用Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)

配置Elasticsearch并重新编入索引后，您便可以升级到2.4。

## 如果您的搜索引擎为 `elasticsearch`

值 `elasticsearch` 表示您的Adobe Commerce或Magento Open Source的下级版本已配置为使用Elasticsearch2.x。不再支持此版本的Elasticsearch。

在升级到2.4之前，您必须执行以下任务：

1. 更新Elasticsearch。 我们建议更新到Elasticsearch7.x。请参阅 [升级Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有关在部署到生产之前备份数据、检测潜在迁移问题和测试升级的完整说明。 根据您当前版本的Elasticsearch，可能需要或不需要完全重新启动群集。

   >[!NOTE]
   >
   >Elasticsearch需要JDK 1.8或更高版本。 请参阅 [安装Java软件开发工具包(JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) 以检查安装的JDK版本。

1. [配置Magento以使用Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html) 和重新编入索引。

配置Elasticsearch并重新编入索引后，您便可以升级到2.4。
