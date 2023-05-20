---
title: 搜尋引擎必要條件
description: 請依照下列步驟，針對Adobe Commerce和Magento Open Source的內部部署安裝安裝並設定支援的搜尋引擎軟體。
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---

# 搜尋引擎必要條件

自Adobe Commerce和Magento Open Source2.4起，所有安裝都必須設定為使用 [Elasticsearch](https://www.elastic.co) 或 [OpenSearch](https://opensearch.org/) 作為目錄搜尋解決方案。

>[!NOTE]
>
>2.4.4版新增OpenSearch支援。OpenSearch是相容的Elasticsearch復本。 設定Elasticsearch7的所有指示都適用於OpenSearch。 [從Elasticsearch移轉至OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 提供切換至OpenSearch的指引。

## 支援的版本

您必須先安裝並設定Elasticsearch或OpenSearch，才能安裝Adobe Commerce 2.4.4和更新版本。

請參閱 [系統需求](../../system-requirements.md) 以取得特定版本資訊。

## 建議的設定

我們建議採取下列步驟：

* [為您的搜尋引擎設定nginx](configure-nginx.md)
* [為您的搜尋引擎設定Apache](configure-apache.md)

## 安裝位置

下列工作假設您已根據下列圖表設定您的系統：

![搜尋引擎圖表](../../../assets/installation/search-engine-config.svg)

上圖顯示：

* Commerce應用程式和搜尋引擎會安裝在不同的主機上。

   在個別主機上執行時需要代理程式才能運作。 (搜尋引擎叢集不在本指南的涵蓋範圍內，但您可以在以下連結中找到更多資訊： [Elasticsearch叢集檔案](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* 每個主機都有自己的網頁伺服器；網頁伺服器不必相同。

   例如，商務應用程式可執行Apache，而搜尋引擎則可執行nginx。

* 這兩部網頁伺服器都使用傳輸層安全性(TLS)。

   設定TLS不屬於我們檔案的範圍。

搜尋請求的處理方式如下：

1. Commerce網頁伺服器會收到來自使用者的搜尋請求，並將請求轉送給搜尋引擎伺服器。

   您可以設定搜尋引擎來連線到Proxy的主機及連線埠。 我們建議使用Web伺服器的SSL連線埠（預設為443）。

1. 搜尋引擎網頁伺服器（在連線埠443上接聽）會代理請求至搜尋引擎伺服器（預設情況下，會在連線埠9200上接聽）。

1. HTTP基本驗證會進一步保護搜尋引擎的存取權。 若要讓請求連線至搜尋引擎，必須透過SSL傳送 *和* 提供有效的使用者名稱和密碼。

1. 搜尋引擎會處理請求。

1. 通訊會沿著相同的路徑傳回，而Elasticsearch網頁伺服器會充當安全的反向Proxy。

## 必要條件

本節中討論的任務需要下列內容：

* [防火牆與SELinux](#firewall-and-selinux)
* [安裝Java軟體開發套件(JDK)](#install-the-java-software-development-kit)
* [安裝搜尋引擎](#install-the-search-engine)
* [升級Elasticsearch](#upgrading-elasticsearch)

### 防火牆與SELinux

安全性相關軟體(iptables、SELinux、AppArmor)預設可設定為封鎖子系統之間的通訊。 檢查它們是否有問題可能是一個好主意。

#### 設定iptables和SELinux的規則

若要設定允許與防火牆或SELinux啟用的通訊的規則，請查閱下列資源：

* [iptables操作說明](https://help.ubuntu.com/community/IptablesHowTo)
* [如何編輯iptables規則（fedora專案）](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [SELinux簡介(CentOS.org)](https://www.centos.org)
* [SELinux How-To Wiki (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### 安裝Java Software Development Kit

若要判斷是否已安裝Java，請輸入下列命令：

```bash
java -version
```

如果訊息 `java: command not found` 顯示，您必須依照下一節所述安裝Java SDK。

請參閱下列其中一節：

* [在CentOS上安裝最新的JDK](#install-the-jdk-on-centos)
* [在Ubuntu上安裝最新的JDK](#install-the-jdk-on-ubuntu)

#### 在CentOS上安裝JDK

檢視此 [數位海洋教學課程](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

請務必安裝JDK及 *not* JRE。

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java 8版可能並非適用於所有作業系統。 例如，您可以 [搜尋Ubuntu的可用套件清單](https://packages.ubuntu.com/).

#### 在Ubuntu上安裝JDK

若要在Ubuntu上安裝JDK 1.8，請以使用者身分輸入以下命令， `root` 許可權：

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

如需其他選項，請參閱 [oracle檔案](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### 安裝搜尋引擎

追隨 [安裝Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) 或 [安裝及設定OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) 平台特定步驟的相關資訊。

若要確認Elasticsearch是否正常運作，請在執行它的伺服器上輸入下列命令：

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

系統會顯示類似下列的訊息：

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

若要驗證OpenSearch是否正常運作，請輸入下列命令：

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## 升級Elasticsearch

請參閱 [升級Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 取得有關備份資料、偵測潛在移轉問題，以及在部署到生產環境之前測試升級的完整指示。 視您目前的Elasticsearch版本而定，不一定需要完全重新啟動叢集。

Elasticsearch需要JDK 1.8或更新版本。 另請參閱 [安裝Java Software Development Kit](#install-the-java-software-development-kit) 以檢查已安裝的JDK版本。

## 其他資源

請參閱 [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) 或 [OpenSearch](https://opensearch.org/docs/latest/) 說明檔案。
