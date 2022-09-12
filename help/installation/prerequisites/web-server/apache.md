---
title: Apache
description: 请按照以下步骤安装和配置Apache Web服务器，以在本地安装Adobe Commerce和Magento Open Source。
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Apache

Adobe Commerce支持Apache 2.4.x。

## Apache必需指令

1. 已设置 `AllowEncodedSlashes` 在服务器配置（全局）或虚拟主机配置中，以避免解码可能导致URL问题的编码斜杠。 例如，在通过API检索SKU中带有斜杠的产品时，您不希望进行转换。 示例块不完整，需要其他指令。

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache重写和htaccess

本主题讨论如何启用Apache 2.4重写，并为 [分布式配置文件， `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe Commerce和Magento Open Source使用服务器重写和 `.htaccess` 提供Apache的目录级说明。 本主题的所有其他部分也包含以下说明。

使用此部分可启用Apache 2.4重写，并为 [分布式配置文件， `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce和Magento Open Source使用服务器重写和 `.htaccess` 提供Apache的目录级说明。

>[!NOTE]
>
>如果未能启用这些设置，通常会导致店面或管理员上不显示样式。

1. 启用Apache重写模块：

   ```bash
   a2enmod rewrite
   ```

1. 使应用程序能够使用 `.htaccess` 配置文件，请参阅 [Apache 2.4文档](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >在Apache 2.4中，服务器的默认站点配置文件为 `/etc/apache2/sites-available/000-default.conf`.

   例如，您可以在的 `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >有时，可能需要其他参数。 有关更多信息，请参阅 [Apache 2.4文档](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. 如果更改了Apache设置，请重新启动Apache:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- 如果您从早期的Apache版本升级，请首先查找 `<Directory "/var/www/html">` 或 `<Directory "/var/www">` in `000-default.conf`.
   >- 您必须更改 `AllowOverride` 在指令中，您希望将Adobe Commerce或Magento Open Source软件安装到的目录。 例如，要在Web服务器Docroot中安装，请在 `<Directory /var/www>`.


>[!NOTE]
>
>如果未能启用这些设置，通常会导致样式无法在店面或管理员中显示。

## Apache所需模块

Adobe Commerce和Magento Open Source需要安装以下Apache模块：

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

结果显示如下所示：

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- 如果Apache为 *not* 已安装，请参阅：
   - [在Ubuntu上安装或升级Apache](#installing-apache-on-ubuntu)
   - [在CentOS上安装Apache](#installing-apache-on-centos)

## 在Ubuntu上安装或升级Apache

以下各节将讨论如何安装或升级Apache:

- 安装Apache
- 在Ubuntu上升级到Apache 2.4以使用PHP 7.4。

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

   结果显示如下所示：

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. 启用 [重写和 `.htaccess`](#apache-rewrites-and-htaccess).

### 在Ubuntu上升级Apache

要升级到Apache 2.4，请执行以下操作：

1. 添加 `ppa:ondrej` 存储库，其中包含Apache 2.4:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. 安装Apache 2.4:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >如果“apt-get install”命令因未满足依赖项而失败，请咨询资源，如 [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. 验证安装。

   ```bash
   apache2 -v
   ```

   应显示与以下内容类似的消息：

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. 启用 [重写和 `.htaccess`](#apache-rewrites-and-htaccess).

## 在CentOS上安装Apache

Adobe Commerce和Magento Open Source需要Apache使用服务器重写。 您还必须指定可以在 `.htaccess`，应用程序使用它指定重写规则。

安装和配置Apache基本上是三步流程：安装软件、启用重写并指定 `.htaccess` 指令。

### 安装Apache

1. 安装Apache 2.4（如果尚未安装）。

   ```bash
   yum -y install httpd
   ```

1. 验证安装：

   ```bash
   httpd -v
   ```

   与以下显示类似的消息，用于确认安装成功：

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. 继续下一节。

   >[!NOTE]
   >
   >即使Apache 2.4默认随CentOS一起提供，请参阅以下部分对其进行配置。

### 为CentOS启用重写和.htaccess

1. 打开 `/etc/httpd/conf/httpd.conf` 要编辑的文件：

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. 找到以下内容开头的块：

   ```conf
   <Directory "/var/www/html">
   ```

1. 更改 `AllowOverride` to `All`.

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
   >的上一个值 `Order` 可能并非在所有情况下都有效。 有关更多信息，请参阅Apache文档([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order))。

1. 保存文件并退出文本编辑器。

1. 要应用Apache设置，请重新启动Apache。

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>如果未能启用这些设置，通常会导致店面或管理员上不显示样式。

### 为Ubuntu启用重写和.htaccess

1. 打开 `/etc/apache2/sites-available/default` 要编辑的文件：

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. 找到以下内容开头的块：

   `<Directory "/var/www/html">`

1. 更改 `AllowOverride` to `All`.

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

1. 配置Apache以使用 `mod_rewrite` 模块：

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

如果在尝试访问站点时遇到403禁止错误，则可以更新Apache配置或虚拟主机配置，以使访客能够访问站点：

### 解决Apache 2.4的403禁止错误

要使网站访客能够访问您的网站，请使用 [需要指令](https://httpd.apache.org/docs/2.4/howto/access.html).

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
>的上一个值 `Order` 可能并非在所有情况下都有效。 有关更多信息，请参阅 [Apache文档](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
