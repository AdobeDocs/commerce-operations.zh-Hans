---
title: AWS OpenSearch
description: 請依照下列步驟，為Adobe Commerce和Magento Open Source的內部部署設定AWS OpenSearch Web服務。
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce和Magento Open Source 2.4.5支援使用Amazon OpenSearch Service叢集。 此服務是AmazonElasticsearch服務的後續服務。 本主題說明如何設定Commerce以使用AWS OpenSearch，以及如何將資料從本機Elasticsearch或OpenSearch執行個體移轉至AWS OpenSearch叢集。

## 建立AWS OpenSearch服務網域

您必須先在AWS中建立OpenSearch執行個體。
讀取 [建立和管理Amazon OpenSearch Service網域](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) 以取得詳細指示。

## 將資料傳入AWS OpenSearch

在AWS上完成所有準備工作後，就可以將資料填入當中了。

對於較小的安裝，我們建議您直接在AWS執行個體上建立索引，原因如下：

* 重新建立索引是一項快速操作。
* 舊執行個體和AWS執行個體之間可能存在版本不相容問題，直接在AWS執行個體上建立可以避免這些不相容問題。

較大型的安裝單位可能會想要考慮將其資料索引從現有執行個體移轉至AWS。 雖然這樣可以減少停機時間，但由於舊版Elasticsearch伺服器與AWS之間的版本不同，因此出現不相容問題的風險仍然很小。

無需移轉索引，因為這些索引可在AWS執行個體上輕鬆重新建立。
不過，移轉資料索引時，請確保Elasticsearch/OpenSearch的版本相容。

請參閱Amazon [移轉至Amazon OpenSearch服務](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) 指示以取得詳細資訊。

### 為OpenSearch設定Commerce

有關設定OpenSearch的步驟，請參見 [進階安裝](../../advanced.md) 主題。

若要測試新設定是否正常運作，請直接測試OpenSearch端點：

1. 在「管理員」中建立產品（例如：sku=&quot;testproduct1&quot;）。
1. 透過管理員重新索引。
1. 查詢OpenSearch端點(可在AWS UI中找到)：

   若要取得索引，請附加： `/_cat/indices/*?v=true` 前往URL：
   `<AWS OS endpoint>/_cat/indices/*?v=true`

若要從索引取得產品，請附加： `/magento2docker_product_1/_search?q=*` 前往URL：
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## 其他資源

如需詳細資訊，請參閱 [OpenSearch AWS檔案](https://docs.aws.amazon.com/opensearch-service/index.html).
