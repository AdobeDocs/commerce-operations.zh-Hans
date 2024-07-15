---
title: AWS OpenSearch
description: 按照以下步骤为Adobe Commerce的内部安装配置AWS OpenSearch Web服务。
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce 2.4.5支持使用Amazon OpenSearch Service群集。 此服务是AmazonElasticsearch服务的后续服务。 本主题介绍如何配置Commerce以使用AWS OpenSearch，以及如何将数据从本地Elasticsearch或OpenSearch实例迁移到AWS OpenSearch集群。

## 创建AWS OpenSearch服务域

您必须首先在AWS中建立OpenSearch实例。
有关详细说明，请参阅[创建和管理Amazon OpenSearch服务域](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html)。

## 将数据获取到AWS OpenSearch

在AWS上完成所有准备工作后，便应该使用数据来填充该数据。

对于较小的安装，我们建议您直接在AWS实例上创建索引，原因如下：

* 重新创建索引是一项快速操作。
* 旧实例和AWS实例之间可能存在版本不兼容性，可以通过直接在AWS实例上构建来避免这些情况。

大型安装可能希望考虑将其数据索引从现有实例迁移到AWS。 虽然这可以减少停机时间，但由于旧Elasticsearch服务器和AWS之间的版本不同，仍然存在出现不兼容问题的较小风险。

无需迁移索引，因为这些索引可以在AWS实例中轻松重新创建。
但是，在迁移数据索引时，请确保Elasticsearch/OpenSearch的版本兼容。

有关详细信息，请参阅Amazon的[迁移到Amazon OpenSearch服务](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html)说明。

### 为OpenSearch配置Commerce

有关配置OpenSearch的步骤，请参见[高级安装](../../advanced.md)主题。

要测试新配置是否正常工作，请直接测试OpenSearch端点：

1. 在管理员中创建产品（例如：sku=&quot;testproduct1&quot;）。
1. 通过管理员重新索引。
1. 查询OpenSearch端点(可在AWS UI中找到)：

   若要获取索引，请将`/_cat/indices/*?v=true`附加到URL：
   `<AWS OS endpoint>/_cat/indices/*?v=true`

要从索引获取产品，请将`/magento2docker_product_1/_search?q=*`附加到URL：
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## 其他资源

有关详细信息，请参阅[OpenSearch AWS文档](https://docs.aws.amazon.com/opensearch-service/index.html)。
