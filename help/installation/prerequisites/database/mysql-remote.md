---
title: 设置远程MySQL数据库连接
description: 按照以下步骤为Adobe Commerce的内部安装配置远程数据库连接。
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# 设置远程MySQL数据库连接

有时，您可能希望将数据库托管在单独的服务器上，而不是在同一台计算机上运行数据库服务器和Web服务器。

Adobe提供了连接到其他计算机上的MySQL服务器的方法。 从Adobe Commerce 2.4.3开始，您还可以将应用程序配置为使用Amazon Web Services (AWS) Aurora数据库，而无需更改代码。

Aurora是托管在AWS上的高性能、完全兼容的MySQL服务器。

## 连接到AWS Aurora数据库

使用Aurora作为数据库与使用默认数据库连接器在一般Adobe Commerce设置配置中指定数据库一样简单。

运行时 `bin/magento setup:install`中，使用Aurora信息 `db-` 字段：

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

此 `db-host` value是带有 `https://` 和结尾 `:portnumber`  已删除。

## 设置远程数据库连接

>[!NOTE]
>
>这是一个高级主题，仅应由经验丰富的网络管理员或数据库管理员使用。 您必须拥有 `root` 访问文件系统，并且您必须能够以 `root`.

### 先决条件

在开始之前，您必须：

* [安装MySQL服务器](mysql.md) 在数据库服务器上。
* [创建数据库实例](mysql.md#configuring-the-database-instance) 在数据库服务器上。
* 在Adobe Commerce Web节点上安装MySQL客户端。 有关详细信息，请参阅MySQL文档。

### 高可用性

如果Web服务器或数据库服务器是群集的，请使用以下准则来配置远程数据库连接：

* 必须为每个Web服务器节点配置一个连接。
* 通常，可以配置到数据库负载平衡器的数据库连接；但是，数据库群集可能会很复杂，具体配置取决于您。 Adobe没有对数据库聚类提出具体的建议。

  有关更多信息，请参阅 [MySQL文档](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### 解决连接问题

如果在连接到任一主机时出现问题，请先ping另一台主机以确保其可访问。 可能需要通过修改防火墙和SELinux规则（如果使用SELinux）来允许从一台主机到另一台主机的连接。

## 创建远程连接

要创建远程连接，请执行以下操作：

1. 在数据库服务器上，作为具有 `root` 权限，打开您的MySQL配置文件。

   要找到它，请输入以下命令：

   ```bash
   mysql --help
   ```

   该位置显示如下：

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >在Ubuntu 16上，路径通常为 `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. 在配置文件中搜索 `bind-address`.

   如果存在，请按如下方式更改值。

   如果该规则不存在，则将其添加到 `[mysqld]` 部分。

   ```conf
   bind-address = <ip address of your web node>
   ```

   请参阅 [MySQL文档](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)，尤其是如果您有群集化的Web服务器。

1. 保存对配置文件所做的更改并退出文本编辑器。
1. 重新启动MySQL服务：

   * CentOS： `service mysqld restart`

   * Ubuntu： `service mysql restart`

   >[!NOTE]
   >
   >如果MySQL无法启动，请在syslog中查找问题的来源。 使用解决问题 [MySQL文档](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) 或其他权威来源。

## 向数据库用户授予访问权限

要使Web节点能够连接到数据库服务器，必须授予Web节点数据库用户访问远程服务器上数据库的权限。

此示例授予 `root` 数据库用户对远程主机上数据库的完全访问权限。

要向数据库用户授予访问权限，请执行以下操作：

1. 登录到数据库服务器。
1. 连接到MySQL数据库，作为 `root` 用户。
1. 输入以下命令：

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   例如，

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >如果Web服务器是群集的，请在每个Web服务器上输入相同的命令。 对于每个Web服务器，必须使用相同的用户名。

## 验证数据库访问权限

在Web节点主机上，输入以下命令以验证连接是否有效：

```bash
mysql -u <local database username> -h <database server ip address> -p
```

如果MySQL监视器显示如下，则数据库已准备好使用Adobe Commerce：

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

如果Web服务器是群集的，请在每个Web服务器主机上输入该命令。

## 安装Adobe Commerce

安装Adobe Commerce时，必须指定以下内容：

* 基本URL(也称为 *商店地址*)指定 *Web节点*
* 数据库主机是 *远程数据库服务器* IP地址（如果数据库服务器是群集的，则使用负载平衡器）
* 数据库用户名是 *本地Web节点* 您授予访问权限的数据库用户
* 数据库口令是本地Web节点用户的口令
* Database name是远程服务器上数据库的名称
