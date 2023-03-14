---
title: 内部部署安装先决条件
description: 详细了解Adobe Commerce和Magento Open Source的内部安装所需的软件依赖项。
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---


# 内部部署安装先决条件

在安装Adobe Commerce或Magento Open Source之前，必须执行以下操作：

* 设置符合以下条件的一个或多个主机： [系统要求](../system-requirements.md).
* 如果要设置多个具有负载平衡的Web节点，请设置并测试系统的该部分 _早于_ 安装应用程序。
* 确保您可以在安装过程中的不同时间点备份整个系统，以便在出现问题时将其回滚。

>[!NOTE]
>
>我们假定您要在中安装Adobe Commerce或Magento Open Source **开发环境**，您具有计算机的超级用户访问权限， **和** 机器不需要高度安全。 如果您正在设置更安全的计算机，我们强烈建议您向网络管理员寻求其他帮助。

我们强烈建议您更新并升级操作系统软件。 这些升级可以提供安全和软件修复，以防止将来出现问题。 不知道这些是什么意思吗？ 查看我们的 [安装概述页面](../overview.md).

以用户身份输入以下命令 `root` 权限：

* 乌本图

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

Adobe Commerce和Magento Open Source支持Apache版本2.4，因为以下结果表示：

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

要安装或升级Apache，请参阅 [Apache](web-server/apache.md).

### PHP

参见 [系统要求](../system-requirements.md) 支持的PHP和版本的信息 [PHP] 有关PHP要求的信息。

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

例如：

```bash
mysql -u magento -p
```

检查您所安装的Adobe Commerce或Magento Open Source的版本是否具有正确的MySQL版本([查看此处以了解支持的版本](../system-requirements.md). 以下结果表示您运行的版本。)

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

验证OpenSearch安装：

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

验证Elasticsearch安装：

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
