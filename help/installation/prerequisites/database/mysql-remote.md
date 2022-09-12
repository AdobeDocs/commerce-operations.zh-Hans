---
title: 设置远程MySQL数据库连接
description: 请按照以下步骤为Adobe Commerce和Magento Open Source的本地安装配置远程数据库连接。
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---


# 设置远程MySQL数据库连接

有时，您可能希望将数据库托管在单独的服务器上，而不是在同一台计算机上运行数据库服务器和Web服务器。

Adobe提供了一种在其他计算机上连接到MySQL服务器的方法。 从Adobe Commerce和Magento Open Source2.4.3开始，您还可以将应用程序配置为使用Amazon Web Services(AWS)Aurora数据库，而无需更改代码。

Aurora是一个高性能、完全兼容的MySQL Server托管在AWS上。

## 连接到AWS Aurora数据库

使用Aurora作为数据库与在常规Adobe Commerce和Magento Open Source设置配置中使用默认数据库连接器指定数据库一样简单。

运行时 `bin/magento setup:install`，请在 `db-` 字段：

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

的 `db-host` 值是带有 `https://` 和尾随 `:portnumber`  已删除。

## 设置远程数据库连接

>[!NOTE]
>
>这是一个高级主题，只应由经验丰富的网络管理员或数据库管理员使用。 您必须 `root` 对文件系统的访问，并且您必须能够以 `root`.

### 先决条件

在开始之前，您必须：

* [安装MySQL服务器](mysql.md) 在数据库服务器上。
* [创建数据库实例](mysql.md#configuring-the-database-instance) 在数据库服务器上。
* 在Adobe Commerce或Magento Open SourceWeb节点上安装MySQL客户端。 有关详细信息，请参阅MySQL文档。

### 高可用性

如果您的Web服务器或数据库服务器已群集化，请使用以下准则配置远程数据库连接：

* 必须为每个Web服务器节点配置连接。
* 通常，您配置与数据库负载平衡器的数据库连接；但是，数据库群集可能非常复杂，配置它取决于您。 Adobe没有对数据库聚类提出具体建议。

   有关更多信息，请参阅 [MySQL文档](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### 解决连接问题

如果在连接到任一主机时遇到问题，请首先对另一台主机执行Ping操作，以确保可以访问该主机。 您可能需要通过修改防火墙和SELinux规则（如果使用SELinux）来允许从一台主机到另一台主机的连接。

## 创建远程连接

要创建远程连接，请执行以下操作：

1. 在数据库服务器上，作为 `root` 权限，打开MySQL配置文件。

   要找到它，请输入以下命令：

   ```bash
   mysql --help
   ```

   位置显示如下所示：

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >在Ubuntu 16中，路径通常为 `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. 搜索配置文件 `bind-address`.

   如果存在，请按如下方式更改值。

   如果不存在，请将其添加到 `[mysqld]` 中。

   ```conf
   bind-address = <ip address of your web node>
   ```

   请参阅 [MySQL文档](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)，特别是当您有群集Web服务器时。

1. 保存对配置文件所做的更改并退出文本编辑器。
1. 重新启动MySQL服务：

   * CentOS: `service mysqld restart`

   * 乌本图： `service mysql restart`
   >[!NOTE]
   >
   >如果MySQL无法启动，请在syslog中查找问题的源。 使用 [MySQL文档](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) 或其他权威来源。

## 授予对数据库用户的访问权限

要使您的Web节点能够连接到数据库服务器，您必须授予Web节点数据库用户对远程服务器上数据库的访问权限。

此示例授予 `root` 数据库用户对远程主机上的数据库具有完全访问权限。

要授予对数据库用户的访问权限，请执行以下操作：

1. 登录到数据库服务器。
1. 连接到MySQL数据库作为 `root` 用户。
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
   >如果Web服务器已群集化，请在每个Web服务器上输入相同的命令。 您必须为每个Web服务器使用相同的用户名。

## 验证数据库访问权限

在Web节点主机上，输入以下命令以验证连接是否正常工作：

```bash
mysql -u <local database username> -h <database server ip address> -p
```

如果MySQL监视器按如下方式显示，则数据库已准备好用于Adobe Commerce或Magento Open Source:

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

如果Web服务器已群集化，请在每个Web服务器主机上输入命令。

## 安装Adobe Commerce或Magento Open Source

安装Adobe Commerce或Magento Open Source时，必须指定以下内容：

* 基地 [URL](https://glossary.magento.com/url) (也称为 *存储地址*)指定的主机名或IP地址 *Web节点*
* 数据库主机是 *远程数据库服务器* IP地址（或者，如果数据库服务器已群集化，则负载平衡器）
* 数据库用户名是 *本地Web节点* 您向其授予访问权限的数据库用户
* 数据库密码是本地Web节点用户的密码
* 数据库名称是远程服务器上数据库的名称
