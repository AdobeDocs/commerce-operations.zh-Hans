---
title: 搜索引擎先决条件
description: 按照以下步骤安装和配置受支持的Adobe Commerce和Magento Open Source本地安装的搜索引擎软件。
feature: Install, Search
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---

# 搜索引擎先决条件

自Adobe Commerce和Magento Open Source2.4起，所有安装都必须配置为使用 [Elasticsearch](https://www.elastic.co) 或 [OpenSearch](https://opensearch.org/) 作为目录搜索解决方案。

>[!NOTE]
>
>2.4.4中添加了OpenSearch支持。OpenSearch是兼容的Elasticsearch分支。 有关配置Elasticsearch7的所有说明均适用于OpenSearch。 [从Elasticsearch迁移到OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 提供了有关切换到OpenSearch的指南。

## 支持的版本

在安装Adobe Commerce 2.4.4及更高版本之前，必须安装和配置Elasticsearch或OpenSearch。

请参阅 [系统要求](../../system-requirements.md) 以了解特定版本信息。

## 推荐的配置

我们建议执行以下操作：

* [为搜索引擎配置nginx](configure-nginx.md)
* [为搜索引擎配置Apache](configure-apache.md)

## 安装位置

以下任务假定您已根据下图配置系统：

![搜索引擎图表](../../../assets/installation/search-engine-config.svg)

上图显示：

* Commerce应用程序和搜索引擎安装在不同的主机上。

  在单独的主机上运行需要代理才能正常工作。 (搜索引擎聚类超出了本指南的范围，但您可以在 [Elasticsearch聚类文档](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* 每台主机都有自己的Web服务器；Web服务器不必相同。

  例如，商务应用程序可以运行Apache，搜索引擎可以运行nginx。

* 两个Web服务器都使用传输层安全性(TLS)。

  设置TLS超出了我们文档的范围。

搜索请求的处理方式如下：

1. Commerce Web服务器接收来自用户的搜索请求，该服务器将其转发到搜索引擎服务器。

   您可以配置搜索引擎以连接到代理的主机和端口。 我们建议Web服务器的SSL端口（默认情况下，443）。

1. 搜索引擎Web服务器（在端口443上侦听）将请求代理到搜索引擎服务器（默认情况下，在端口9200上侦听）。

1. HTTP基本身份验证进一步保护对搜索引擎的访问。 对于到达搜索引擎的请求，必须通过SSL传输 *和* 提供有效的用户名和密码。

1. 搜索引擎处理请求。

1. 通信沿同一路径返回，ElasticsearchWeb服务器充当安全反向代理。

## 先决条件

本节中讨论的任务需要满足以下条件：

* [防火墙和SELinux](#firewall-and-selinux)
* [安装Java软件开发工具包(JDK)](#install-the-java-software-development-kit)
* [安装搜索引擎](#install-the-search-engine)
* [升级Elasticsearch](#upgrading-elasticsearch)

### 防火墙和SELinux

默认情况下，可以将安全相关软件(iptables、SELinux、AppArmor)配置为阻止子系统之间的通信。 检查他们是否有问题可能是一个好主意。

#### 为iptables和SELinux设置规则

要设置规则以允许与启用防火墙或SELinux进行通信，请查阅以下资源：

* [iptables操作说明](https://help.ubuntu.com/community/IptablesHowTo)
* [如何编辑iptables规则（fedora项目）](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [SELinux简介(CentOS.org)](https://www.centos.org)
* [SELinux操作方法维客(CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### 安装Java软件开发工具包

要确定是否已安装Java，请输入以下命令：

```bash
java -version
```

如果消息 `java: command not found` 显示时，您必须按照下一节中讨论的内容安装Java SDK。

请参阅以下部分之一：

* [在CentOS上安装最新的JDK](#install-the-jdk-on-centos)
* [在Ubuntu上安装最新的JDK](#install-the-jdk-on-ubuntu)

#### 在CentOS上安装JDK

查看此 [数字海洋教程](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

请务必安装JDK和 *非* JRE。

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java版本8可能并不适用于所有操作系统。 例如，您可以 [搜索Ubuntu的可用包列表](https://packages.ubuntu.com/).

#### 在Ubuntu上安装JDK

要在Ubuntu上安装JDK 1.8，请以用户身份输入以下命令， `root` 权限：

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

有关其他选项，请参阅 [oracle文档](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### 安装搜索引擎

关注 [安装Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) 或 [安装和配置OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) 执行特定于平台的步骤。

要验证Elasticsearch是否正常工作，请在运行该服务器的服务器上输入以下命令：

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

将显示类似于以下内容的消息：

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

要验证OpenSearch是否正常工作，请输入以下命令：

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## 升级Elasticsearch

请参阅 [升级Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有关备份数据、检测潜在迁移问题以及测试升级以便部署到生产环境之前的完整说明。 根据您当前的Elasticsearch版本，可能需要也可能不需要完全重新启动群集。

Elasticsearch需要JDK 1.8或更高版本。 请参阅 [安装Java软件开发工具包](#install-the-java-software-development-kit) 以检查已安装的JDK版本。

## 其他资源

请参阅 [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) 或 [OpenSearch](https://opensearch.org/docs/latest/) 文档。
