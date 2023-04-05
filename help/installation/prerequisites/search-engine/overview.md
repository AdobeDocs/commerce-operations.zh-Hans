---
title: 搜索引擎先决条件
description: 请按照以下步骤安装和配置支持的搜索引擎软件，以在本地安装Adobe Commerce和Magento Open Source。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---


# 搜索引擎先决条件

自Adobe Commerce和Magento Open Source2.4起，必须将所有安装配置为使用 [Elasticsearch](https://www.elastic.co) 或 [OpenSearch](https://opensearch.org/) 作为目录搜索解决方案。

>[!NOTE]
>
>2.4.4中添加了OpenSearch支持。 OpenSearch是一个兼容的分支Elasticsearch。 配置Elasticsearch7的所有说明都适用于OpenSearch。 [从Elasticsearch迁移到OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 提供有关切换到OpenSearch的指导。

## 支持的版本

安装Adobe Commerce 2.4.4及更高版本之前，必须安装并配置OpenSearch或OpenSearch。

请参阅 [系统要求](../../system-requirements.md) 以了解特定版本信息。

## 建议的配置

我们建议执行以下操作：

* [为搜索引擎配置nginx](configure-nginx.md)
* [为搜索引擎配置Apache](configure-apache.md)

## 安装位置

以下任务假定您已根据下图配置了系统：

![搜索引擎图](../../../assets/installation/search-engine-config.svg)

上图显示：

* 商务应用程序和搜索引擎安装在不同的主机上。

   在单独的主机上运行需要代理才能正常工作。 (对搜索引擎进行聚类超出了本指南的范围，但您可以在 [Elasticsearch聚类文档](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* 每台主机都有自己的Web服务器；web服务器不必是相同的。

   例如，商务应用程序可以运行Apache，而搜索引擎可以运行nginx。

* 两个Web服务器都使用传输层安全性(TLS)。

   设置TLS不在文档的范围之内。

搜索请求的处理方式如下：

1. 商务Web服务器接收用户的搜索请求，该服务器将其转发到搜索引擎服务器。

   可将搜索引擎配置为连接到代理的主机和端口。 我们建议使用Web服务器的SSL端口（默认为443）。

1. 搜索引擎Web服务器（监听端口443）将请求代理到搜索引擎服务器（默认情况下，它监听端口9200）。

1. HTTP Basic身份验证进一步保护对搜索引擎的访问。 要请求访问搜索引擎，必须通过SSL传输 *和* 提供有效的用户名和密码。

1. 搜索引擎处理请求。

1. 通信沿同一路由返回，ElasticsearchWeb服务器充当安全反向代理。

## 先决条件

本节中讨论的任务需要满足以下条件：

* [防火墙和SELinux](#firewall-and-selinux)
* [安装Java软件开发工具包(JDK)](#install-the-java-software-development-kit)
* [安装搜索引擎](#install-the-search-engine)
* [升级Elasticsearch](#upgrading-elasticsearch)

### 防火墙和SELinux

与安全相关的软件(iptables、SELinux、AppArmor)默认可配置为阻止子系统之间的通信。 如果有问题，检查它们可能是个好主意。

#### 为iptables和SELinux设置规则

要设置规则以允许与已启用防火墙或SELinux的通信，请查阅以下资源：

* [iptables操作方法](https://help.ubuntu.com/community/IptablesHowTo)
* [如何编辑Iptables规则（fedora项目）](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [SELinux简介(CentOS.org)](https://www.centos.org)
* [SELinux操作维基(CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### 安装Java软件开发工具包

要确定是否已安装Java，请输入以下命令：

```bash
java -version
```

如果消息 `java: command not found` 显示，您必须按照下一节中所述安装Java SDK。

请参阅以下部分之一：

* [在CentOS上安装最新的JDK](#install-the-jdk-on-centos)
* [在Ubuntu上安装最新的JDK](#install-the-jdk-on-ubuntu)

#### 在CentOS上安装JDK

请参阅 [数字海洋教程](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

请务必安装JDK和 *not* JRE。

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java版本8可能并非适用于所有操作系统。 例如，您可以 [搜索Ubuntu的可用包列表](https://packages.ubuntu.com/).

#### 在Ubuntu上安装JDK

要在Ubuntu上安装JDK 1.8，请以用户身份输入以下命令 `root` 权限：

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

有关其他选项，请参阅 [Oracle文档](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### 安装搜索引擎

关注 [安装Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) 或 [安装和配置OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) 的步骤。

要验证Elasticsearch是否正常工作，请在运行该服务器的服务器上输入以下命令：

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

将显示一条与以下内容类似的消息：

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

请参阅 [升级Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) 有关在部署到生产之前备份数据、检测潜在迁移问题和测试升级的完整说明。 根据您当前版本的Elasticsearch，可能需要或不需要完全重新启动群集。

Elasticsearch需要JDK 1.8或更高版本。 请参阅 [安装Java软件开发工具包](#install-the-java-software-development-kit) 以检查安装的JDK版本。

## 其他资源

请参阅 [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) 或 [OpenSearch](https://opensearch.org/docs/latest/) 文档。
