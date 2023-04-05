---
title: 可选软件
description: 进一步了解可安装的可选软件，以支持在本地安装Adobe Commerce和Magento Open Source。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# 可选软件

我们强烈建议您安装NTP以确保与CRON相关的任务正常执行。 （例如，服务器日期可以是过去或将来的日期。）

本主题中讨论的其他可选实用程序可能有助于您进行安装；但是，安装或使用Adobe Commerce或Magento Open Source时不需要使用它们。

## 安装和配置网络时间协议(NTP)

[NTP](https://www.ntp.org/) 使服务器能够使用 [全局可用的池服务器](https://www.ntppool.org/en/). 我们建议您使用您信任的NTP服务器，无论它们是内部网络的专用硬件解决方案还是外部公共服务器。

如果要在多台主机上部署Adobe Commerce或Magento Open Source，则NTP是确保其时钟全部同步的简单方法，无论服务器位于何时区。 此外，与cron相关的任务（如索引和事务性电子邮件）取决于服务器时钟是否准确。

### 在Ubuntu上安装和配置NTP

输入以下命令以安装NTP:

```bash
apt-get install ntp
```

继续 [使用NTP池服务器](#use-ntp-pool-servers).

### 在CentOS上安装和配置NTP

要安装和配置NTP，请执行以下操作：

1. 输入以下命令以查找相应的NTP软件：

   ```bash
   yum search ntp
   ```

1. 选择要安装的包。 例如， `ntp.x86_64`.

1. 安装包。

   ```bash
   yum -y install ntp.x86_64
   ```

1. 输入以下命令，以便NTP在服务器启动时启动。

   ```bash
   chkconfig ntpd on
   ```

1. 继续下一节。

### 使用NTP池服务器

选择池服务器由您来决定。 如果您使用NTP池服务器，则ntp.org建议您使用 [池服务器](https://www.ntppool.org/en/) 接近您服务器的时区，如 [“NTP池项目”页](https://www.ntppool.org/en/use.html). 如果您有一个专用NTP服务器，该服务器可用于部署中的所有主机，则可以改用该服务器。

1. 打开 `/etc/ntp.conf` 在文本编辑器中。

1. 查找与以下类似的行：

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. 替换这些行或添加指定NTP池服务器或其他NTP服务器的其他行。 最好指定多个。

1. 使用三台基于美国的NTP服务器的示例如下：

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. 将更改保存到 `/etc/ntp.conf` 并退出文本编辑器。

1. 重新启动服务。

   * 乌本图： `service ntp restart`

   * CentOS: `service ntpd restart`

1. 输入 `date` 来检查服务器的日期。

   如果日期不正确，请确保在防火墙中打开NTP客户端端口（通常为UDP 123）。

   尝试 `ntpdate _[pool server hostname]_` 命令。 如果失败，请搜索返回的错误。

   如果其他所有操作都失败，请尝试重新启动服务器。

## 创建phpinfo.php

的 [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) 文件会显示有关PHP及其扩展的大量信息。

>[!NOTE]
>
>使用 `phpinfo.php` 在开发系统中 _仅_. 它可能是生产中的安全问题。

在Web服务器的Docroot中的任意位置添加以下代码：

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

有关更多信息，请参阅 [phpinfo手册页](https://www.php.net/manual/en/function.phpinfo.php).

要查看结果，请在浏览器的位置或地址字段中输入以下URL:

```http
http://<web server host or IP>/phpinfo.php
```

如果显示404（未找到）错误，请检查以下内容：

* 如有必要，启动Web服务器。
* 确保防火墙允许端口80上的流量。

   [Ubuntu帮助](https://help.ubuntu.com/community/UFW)

   [CentOS帮助](https://wiki.centos.org/HowTos/Network/IPTables)

## phpMyAdmin

phpMyAdmin应用程序是一个易于使用且免费的数据库管理实用程序。 您可以使用它检查和操作数据库的内容。 您必须以MySQL数据库管理用户的身份登录phpMyAdmin。

有关phpMyAdmin的更多信息，请参阅 [phpMyAdmin主页](https://www.phpmyadmin.net/).

有关安装的更多详细信息，请参阅 [phpMyAdmin安装文档](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>在开发系统中使用phpMyAdmin _仅_. 它可能是生产中的安全问题。

1. 要使用phpMyAdmin，请在浏览器的地址或位置字段中输入以下命令：

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. 出现提示时，使用MySQL数据库登录 `root` 或管理用户的用户名和密码。
