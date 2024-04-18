---
title: 当前搜索引擎不受支持
description: 在遇到有关不受支持的搜索引擎的错误后，对Adobe Commerce升级进行故障排除。
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# 当前搜索引擎不受支持

以下错误消息指示您要升级的Adobe Commerce版本配置为使用目录搜索引擎，而您要升级到的版本不支持该目录搜索引擎：

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

此错误表示在Adobe Commerce的较低版本上，出现以下情况之一：

- 搜索引擎设置为MySQL。
- 搜索引擎设置为不再受支持的Elasticsearch版本。

使用以下命令检查当前搜索引擎：

```bash
bin/magento config:show catalog/search/engine
```

如果返回的值是 `mysql`， `elasticsearch`，或 `elasticsearch6`.

>[!WARNING]
>
>如果您收到此错误，则表明您的安装处于不一致状态，并且无法访问管理员。 我们建议您在解决此错误时还原到之前的版本。 为此，请运行以下命令之一：
>
>```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>位置 `<version>` 是您运行的Magento版本 **早于** 升级。 例如， `2.3.5`.

请遵循以下各节中所述的准则，从不一致状态中恢复。

## 如果您的搜索引擎为 `mysql`

在2.4之前，MySQL是默认的目录搜索引擎，但此容量已不再支持MySQL。 现在，在升级到2.4之前，您必须将Elasticsearch或OpenSearch安装并配置为您的搜索引擎。

请使用以下资源来帮助您完成此过程：

- [安装和配置搜索引擎](../../configuration/search/overview-search.md)
- [搜索引擎配置](../../configuration/search/configure-search-engine.md)

配置搜索引擎并重新索引后，即可升级到2.4。

## 如果您的搜索引擎为 `elasticsearch`

不再支持Elasticsearch6及更早版本。

值 `elasticsearch` 指示您的Adobe Commerce低级版本配置为使用Elasticsearch2.x。不再支持此版本的Elasticsearch。

升级到2.4之前，必须执行以下任务：

1. 更新到Commerce支持的Elasticsearch版本。 请参阅 [升级Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有关备份数据、检测潜在迁移问题以及测试升级以便部署到生产环境之前的完整说明。 根据您当前的Elasticsearch版本，可能需要也可能不需要完全重新启动群集。

   >[!NOTE]
   >
   >Elasticsearch需要JDK 1.8或更高版本。 请参阅 [安装Java软件开发工具包(JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) 以检查已安装的JDK版本。

1. [配置Elasticsearch](../../configuration/search/configure-search-engine.md) 并重新索引。

配置搜索引擎并重新索引后，即可升级到2.4。
