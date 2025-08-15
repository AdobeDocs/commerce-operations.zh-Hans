---
title: Apache
description: 按照以下步骤为Adobe Commerce的内部安装安装和配置Apache Web Server。
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: f8c5d714a4e96d0508f745d1b7617696c8cc94a7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerce支持Apache 2.4.x。

## Apache必需指令

1. 在服务器配置（全局）或虚拟主机配置中设置`AllowEncodedSlashes`，以避免解码可能导致URL问题的编码斜杠。 例如，当通过API在SKU中检索具有斜杠的产品时，不希望进行转换。 示例块不完整，需要其他指令。

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache重写和htaccess

本主题讨论如何启用Apache 2.4重写并为[分布式配置文件`.htaccess`](https://github.com/magento/magento2/blob/2.4-develop/.htaccess.sample)指定设置。

Adobe Commerce使用服务器重写和`.htaccess`为Apache提供目录级说明。 以下说明也包含在本主题的所有其他部分中。

使用此部分启用Apache 2.4重写并指定[分布式配置文件`.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)的设置

Adobe Commerce使用服务器重写和`.htaccess`为Apache提供目录级说明。

>[!NOTE]
>
>如果未启用这些设置，通常会导致您的店面或管理员上不显示任何样式。

1. 启用Apache重写模块：

   ```bash
   a2enmod rewrite
   ```

1. 要使应用程序能够使用分布式`.htaccess`配置文件，请参阅[Apache 2.4文档](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)中的准则。

   >[!TIP]
   >
   >在Apache 2.4中，服务器的默认站点配置文件为`/etc/apache2/sites-available/000-default.conf`。

   例如，您可以在`000-default.conf`的末尾添加以下内容：

   ```
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >有时，可能需要其他参数。 有关详细信息，请参阅[Apache 2.4文档](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)。

1. 如果更改了Apache设置，请重新启动Apache：

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- 如果您从早期的Apache版本升级，请在`<Directory "/var/www/html">`中首先查找`<Directory "/var/www">`或`000-default.conf`。
   >- 对于要安装Adobe Commerce软件的目录，必须在指令中更改`AllowOverride`的值。 例如，要在Web服务器docroot中安装，请在`<Directory /var/www>`中编辑该指令。

>[!NOTE]
>
>无法启用这些设置通常会导致样式无法在店面或管理员中显示。

## Apache必需模块

Adobe Commerce需要安装以下Apache模块：

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## 验证Apache版本

要验证您当前运行的Apache版本，请输入：

```bash
apache2 -v
```

显示的结果类似于以下内容：

```
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- 如果Apache是&#x200B;*未安装*，请参阅：
   - [在Ubuntu上安装或升级Apache](#installing-apache-on-ubuntu)
   - [在CentOS上安装Apache](#installing-apache-on-centos)

## 在Ubuntu上安装或升级Apache

以下部分讨论如何安装或升级Apache：

- 安装Apache
- 升级到Ubuntu上的Apache 2.4以使用PHP 7.4。

### 在Ubuntu上安装Apache

要安装默认版本的Apache，请执行以下操作：

1. 安装Apache

   ```bash
   apt-get -y install apache2
   ```

1. 验证安装。

   ```bash
   apache2 -v
   ```

   显示的结果类似于以下内容：

   ```
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. 启用[重写和`.htaccess`](#apache-rewrites-and-htaccess)。

### 在Ubuntu上升级Apache

要升级到Apache 2.4，请执行以下操作：

1. 添加具有Apache 2.4的`ppa:ondrej`存储库：

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. 安装Apache 2.4：

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >如果“apt-get install”命令因未满足的依赖项而失败，请查阅[https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)之类的资源。

1. 验证安装。

   ```bash
   apache2 -v
   ```

   应显示类似于以下内容的消息：

   ```
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. 启用[重写和`.htaccess`](#apache-rewrites-and-htaccess)。

## 在CentOS上安装Apache

Adobe Commerce要求重写Apache Server。 还必须指定可在`.htaccess`中使用的指令类型，应用程序将使用该指令指定重写规则。

安装和配置Apache基本上是一个三步过程：安装软件、启用重写并指定`.htaccess`指令。

### 安装Apache

1. 安装Apache 2.4（如果尚未安装）。

   ```bash
   yum -y install httpd
   ```

1. 验证安装：

   ```bash
   httpd -v
   ```

   类似于以下内容的消息显示以确认安装成功：

   ```
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. 继续下一部分。

   >[!NOTE]
   >
   >即使Apache 2.4默认随CentOS提供，请参阅以下部分以配置它。

### 为CentOS启用重写和.htaccess

1. 打开`/etc/httpd/conf/httpd.conf`文件进行编辑：

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. 找到以下列开头的块：

   ```conf
   <Directory "/var/www/html">
   ```

1. 将`AllowOverride`的值更改为`All`。

   例如，

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >`Order`的前述值可能并非在所有情况下都有效。 有关详细信息，请参阅Apache文档([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order))。

1. 保存文件并退出文本编辑器。

1. 要应用Apache设置，请重新启动Apache。

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>如果未启用这些设置，通常会导致您的店面或管理员上不显示任何样式。

### 为Ubuntu启用重写和.htaccess

1. 打开`/etc/apache2/sites-available/default`文件进行编辑：

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. 找到以下列开头的块：

   `<Directory "/var/www/html">`

1. 将`AllowOverride`的值更改为`All`。

   例如：

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. 保存文件并退出文本编辑器。

1. 配置Apache以使用`mod_rewrite`模块：

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. 重新启动Apache以应用更改：

   ```bash
   service apache2 restart
   ```

## 解决403（禁止）错误

如果您在尝试访问站点时遇到403禁止错误，则可以更新Apache配置或虚拟主机配置以启用站点的访客：

### 解决Apache 2.4的403禁止错误

若要使网站访客能够访问您的网站，请使用[Require指令](https://httpd.apache.org/docs/2.4/howto/access.html)之一。

例如：

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>`Order`的前述值可能并非在所有情况下都有效。 有关详细信息，请参阅[Apache文档](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)。
