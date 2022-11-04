---
title: AWS OpenSearch
description: 请按照以下步骤为Adobe Commerce和Magento Open Source的本地安装配置AWS OpenSearch Web服务。
source-git-commit: 3692dcfd5b50c2f036b005d40a22db061b9ea5fd
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# AWS OpenSearch

Adobe Commerce和Magento Open Source2.4.5支持使用Amazon OpenSearch Service群集。 此服务是AmazonElasticsearch服务的后继服务。 本主题介绍如何配置Commerce以使用AWS OpenSearch，以及如何将数据从本地Elasticsearch或OpenSearch实例迁移到AWS OpenSearch群集。

## 创建AWS OpenSearch服务域

您必须先在AWS中建立OpenSearch实例。
读取 [创建和管理Amazon OpenSearch服务域](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) 以了解详细说明。

## 将数据获取到AWS OpenSearch

在AWS上做好一切准备后，便应使用数据填充数据。

对于较小的安装，我们建议您直接在AWS实例上创建索引，原因如下：

* 重新创建索引是一个快速操作。
* 旧实例与AWS实例之间可能存在版本不兼容问题，直接在AWS实例上构建可以避免这些不兼容问题。

较大的安装可能希望考虑将其数据索引从现有实例迁移到AWS。 虽然这可能减少停机时间，但由于旧Elasticsearch服务器与AWS之间的版本不同，仍然存在出现不兼容问题的小风险。

无需迁移索引，因为可以轻松地在AWS实例上重新创建索引。
但是，在迁移数据索引时，请确保Elasticsearch/OpenSearch的版本兼容。

请参阅Amazon [迁移到Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) 有关详细信息的说明。

### 为OpenSearch配置商务

有关配置OpenSearch的步骤，请参阅 [高级安装](../../advanced.md) 主题。

要测试新配置是否正常工作，请直接测试OpenSearch端点：

1. 在管理员中创建产品(例如：sku=&quot;testproduct1&quot;)。
1. 通过管理员重新编入索引。
1. 查询OpenSearch端点(可在AWS UI中找到):

   要获取索引，请附加： `/_cat/indices/*?v=true` 到URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

要从索引获取产品，请附加： `/magento2docker_product_1/_search?q=*` 到URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## 其他资源

有关其他信息，请参阅 [OpenSearch AWS文档](https://docs.aws.amazon.com/opensearch-service/index.html).
