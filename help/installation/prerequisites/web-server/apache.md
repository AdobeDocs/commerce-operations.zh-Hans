---
title: 为内部部署安装Apache
description: 了解如何为本地Adobe Commerce部署安装和配置Apache。 启用所需的模块、重写和“.htaccess”设置。
feature: Install, Configuration
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# 安装Apache以进行内部部署 {#apache}

本指南将指导您完成为Adobe Commerce内部部署安装Apache以及配置Commerce所需的Apache设置。 它包括共享的Apache要求以及Ubuntu和CentOS特定于操作系统的过程。 Adobe建议遵循本指南中提供的配置说明，以保留Commerce应用程序的功能和安全性。

Adobe支持您的Adobe Commerce版本的[系统要求](../../system-requirements.md)中列出的Apache版本。 支持的版本因版本而异。 Apache还需要支持的PHP配置。 有关相关的PHP要求，请参阅[PHP设置](../php-settings.md)。

从与您的环境匹配的部分开始：

- 如果已安装Apache，请首先查看[Apache要求](#review-apache-requirements)。
- 如果需要在Ubuntu上安装或升级Apache，请转到[在Ubuntu上安装或升级Apache](#installing-or-upgrading-apache-on-ubuntu)。
- 如果需要在CentOS上安装Apache，请转到[在CentOS上安装Apache](#installing-apache-on-centos)。

## 查看Apache要求

在托管Adobe Commerce的任何Apache Server上完成这些要求。

### 配置必需指令

在服务器配置（全局）或虚拟主机配置中设置`AllowEncodedSlashes`，以避免解码可能导致URL问题的编码斜杠。 例如，当通过API在SKU中检索具有斜杠的产品时，不希望转换斜杠。 以下示例块不完整，需要其他指令。

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### 配置rewrites和.htaccess {#apache-rewrites-and-htaccess}

使用此部分启用Apache重写并配置[分布式`.htaccess`文件](https://httpd.apache.org/docs/current/howto/htaccess.html)。 Adobe Commerce使用服务器重写和`.htaccess`为Apache提供目录级说明。

>[!IMPORTANT]
>
>如果未启用这些设置，通常会导致您的店面或管理员上不显示任何样式。 它还可以阻止Apache应用`.htaccess`中定义的Adobe Commerce安全保护。

1. 启用Apache重写模块：

   ```bash
   a2enmod rewrite
   ```

1. 启用应用程序以使用分布式`.htaccess`配置文件。

   1. 在Ubuntu上，编辑`/etc/apache2/sites-available/000-default.conf`。 有关其他Apache布局或如果需要其他参数，请参阅[Apache文档](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)和[Apache访问控制文档](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)。

   1. 为计划安装Adobe Commerce的目录添加或更新`AllowOverride`指令。

   例如，如果在默认`docroot`中安装Adobe Commerce，请将以下块添加到`000-default.conf`：

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >如果您从较早的Apache版本升级，请先在`<Directory "/var/www/html">`中查找现有的`<Directory "/var/www">`或`000-default.conf`块。 如果在其他`docroot`中安装Adobe Commerce，请更新该路径对应的`<Directory>`块。

1. 重新启动Apache以应用更改：

   ```bash
   service apache2 restart
   ```

### 安装所需模块

Adobe Commerce需要安装以下Apache模块：

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## 验证是否已安装Apache

要验证是否已安装Apache并查看当前版本，请输入：

```bash
apache2 -v
```

结果将显示与以下内容类似的信息：

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- 如果Apache是&#x200B;*未安装*，请参阅：
   - [在Ubuntu上安装或升级Apache](#installing-or-upgrading-apache-on-ubuntu)
   - [在CentOS上安装Apache](#installing-apache-on-centos)

## 在Ubuntu上安装或升级Apache {#installing-or-upgrading-apache-on-ubuntu}

在Ubuntu上安装和配置Apache的过程分为三步：

1. 安装软件。
1. 启用重写。
1. 指定`.htaccess`指令。

在配置Apache Server重写时，必须指定可在`.htaccess`中使用的指令类型，应用程序将使用该指令指定重写规则和安全保护。

### 在Ubuntu上安装Apache

1. 安装Apache（如果尚未安装）：

   ```bash
   apt-get -y install apache2
   ```

1. 验证安装：

   ```bash
   apache2 -v
   ```

   类似于以下内容的消息显示以确认安装成功：

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. 继续下一部分。

   >[!NOTE]
   >
   >即使Apache默认随Ubuntu提供，请参阅以下部分以配置它。

### 在Ubuntu上升级Apache

如果已安装Apache并且您使用的版本低于`2.4`，请升级到Apache `2.4`或您部署的Adobe Commerce版本支持的最新版本。 请参阅[系统要求](../../system-requirements.md)。

1. 更新包信息：

   ```bash
   apt-get -y update
   ```

1. 如果需要，添加为您的环境提供受支持Apache版本的存储库。

1. 安装或升级Apache：

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >如果`apt-get install`命令因未满足的依赖项而失败，请查阅操作系统包文档或分发支持资源。

1. 验证安装：

   ```bash
   apache2 -v
   ```

1. 在[系统要求](../../system-requirements.md)中，确认安装的版本与Adobe Commerce版本支持的版本匹配。

1. 为Ubuntu[启用`.htaccess`重写和](#enable-rewrites-and-htaccess-for-ubuntu)。

### 为Ubuntu启用重写和.htaccess

1. 打开`/etc/apache2/sites-available/000-default.conf`文件进行编辑：

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. 找到以下列开头的块：

   ```conf
   <Directory "/var/www/html">
   ```

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

>[!IMPORTANT]
>
>如果未启用这些设置，通常会导致您的店面或管理员上不显示任何样式。 它还可以阻止Apache应用`.htaccess`中定义的Adobe Commerce安全保护。

## 在CentOS上安装Apache {#installing-apache-on-centos}

在CentOS上安装和配置Apache的过程分为三步：

1. 安装软件
2. 启用重写
3. 指定`.htaccess`指令。

在配置Apache Server重写时，必须指定可在`.htaccess`中使用的指令类型，应用程序将使用该指令指定重写规则和安全保护。

### 安装Apache

1. 安装Apache（如果尚未安装）。

   ```bash
   yum -y install httpd
   ```

1. 验证安装：

   ```bash
   httpd -v
   ```

   类似于以下内容的消息显示以确认安装成功：

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. 继续下一部分。

   >[!NOTE]
   >
   >即使Apache默认随CentOS提供，请参阅以下部分以配置它。

### 为CentOS启用重写和.htaccess

1. 打开`/etc/httpd/conf/httpd.conf`文件进行编辑：

   ```bash
   vim /etc/httpd/conf/httpd.conf
   ```

1. 找到以下列开头的块：

   ```conf
   <Directory "/var/www/html">
   ```

1. 将`AllowOverride`的值更改为`All`。

   例如：

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
   >`Order`的前述值可能并非在所有情况下都有效。 有关详细信息，请参阅[Apache文档](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)。

1. 保存文件并退出文本编辑器。

1. 要应用Apache设置，请重新启动Apache。

   ```bash
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>如果未启用这些设置，通常会导致您的店面或管理员上不显示任何样式。 它还可以阻止Apache应用`.htaccess`中定义的Adobe Commerce安全保护。

## 解决403（禁止）错误

如果您在尝试访问站点时遇到403禁止错误，则可以更新Apache配置或虚拟主机配置以启用站点的访客：

### 解决Apache的403禁止错误

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
