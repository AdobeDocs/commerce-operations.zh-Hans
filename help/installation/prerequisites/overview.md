---
title: 内部部署安装先决条件
description: 详细了解Adobe Commerce的内部安装所需的软件依赖项。
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 1%

---

# 内部部署安装先决条件

在安装Adobe Commerce之前，必须执行以下操作：

* 设置一个或多个符合条件的主机 [系统要求](../system-requirements.md).
* 如果要设置多个具有负载平衡的Web节点，请设置并测试系统的该部分 _早于_ 安装应用程序。
* 确保您可以在安装过程中的不同时刻备份整个系统，以便在出现问题时回滚系统。

>[!NOTE]
>
>我们假定您将在以下位置安装Adobe Commerce： **开发环境**，您具有计算机的超级用户访问权限， **和** 机器不需要高度安全。 如果您正在设置更安全的计算机，我们强烈建议您向网络管理员寻求其他帮助。

我们强烈建议您更新和升级操作系统软件。 这些升级可提供安全和软件修复，以防止将来出现问题。 不知道这些是什么意思吗？ 查看我们的 [安装概述页面](../overview.md).

以用户身份输入以下命令 `root` 权限：

* 乌班图

  ```bash
  apt-get update
  ```

  ```bash
  apt-get upgrade
  ```

* CentOS

  ```bash
  yum -y update
  ```

  ```bash
  yum -y upgrade
  ```

## 先决条件检查

要检查系统是否满足先决条件，请输入以下命令：

### Apache

CentOS： `httpd -v`

Ubuntu： `apache2 -v`

Adobe Commerce支持Apache版本2.4，因为以下结果表示：

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

要安装或升级Apache，请参阅 [Apache](web-server/apache.md).

### PHP

请参阅 [系统要求](../system-requirements.md) 支持的PHP和版本 [PHP](../system-requirements.md#php-settings) PHP要求。

### MySQL

检查您是否有兼容的MySQL版本以用于要安装的Adobe Commerce版本。 请参阅 [系统要求](../system-requirements.md) 支持的版本。

```bash
mysql -u <database root user or database owner name> -p
```

例如：

```bash
mysql -u magento -p
```

以下结果指示您正在运行的版本。

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

类型 `help` 或 `\h` 以寻求帮助。 类型 `\c` 以清除当前输入语句。

输入 `exit` 在 `mysql>` 提示退出。

要安装或升级MySQL，请参见 [MySQL](database/mysql.md).

### 搜索引擎

要验证OpenSearch安装，请执行以下操作：

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

要验证Elasticsearch安装，请执行以下操作：

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

例如：

```bash
curl -XGET 'localhost:9200'
```

```terminal
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```
