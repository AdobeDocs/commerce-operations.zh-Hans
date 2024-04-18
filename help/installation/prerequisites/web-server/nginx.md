---
title: 恩金克斯
description: 按照以下步骤安装和配置Nginx Web服务器，以便在Adobe Commerce中进行本地安装。
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---

# 恩金克斯

Adobe Commerce支持nginx 1.x(或 [最新主行版本](https://nginx.org/en/linux_packages.html#mainline))。 您还必须安装最新版本的 `php-fpm`.

安装说明因您使用的操作系统而异。 请参阅 [PHP](../php-settings.md) 了解相关信息。

## 乌班图

以下部分介绍了如何使用nginx、PHP和MySQL在Ubuntu上安装Adobe Commerce 2.x。

### 安装nginx

```bash
sudo apt -y install nginx
```

您还可以 [从源构建nginx](https://www.armanism.com/blog/install-nginx-on-ubuntu)

完成以下部分并安装应用程序后，我们将使用示例配置文件来 [配置nginx](#configure-nginx).

### 安装和配置php-fpm

Adobe Commerce需要多个 [PHP扩展](../php-settings.md) 才能正常运行。 除了这些扩展之外，您还必须安装和配置 `php-fpm` 扩展名一起使用。

安装和配置 `php-fpm`：

1. 安装 `php-fpm` 和 `php-cli`：

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >此命令安装最新可用版本的PHP 7.2.X。请参阅 [系统要求](../../system-requirements.md) 支持的PHP版本。

1. 打开 `php.ini` 编辑器中的文件：

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. 编辑这两个文件以匹配以下行：

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >测试Adobe Commerce时，我们建议将内存限制设置为2 G。 请参阅 [必需的PHP设置](../php-settings.md) 以了解更多信息。

1. 保存并退出编辑器。

1. 重新启动 `php-fpm` 服务：

   ```bash
   systemctl restart php7.2-fpm
   ```

### 安装和配置MySQL

请参阅 [MySQL](../database/mysql.md) 以了解更多信息。

### 安装和配置

有多种下载Adobe Commerce的方法，包括：

* [获取Composer隐含](../../composer.md)

* [克隆Git存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

此示例显示了使用命令行进行的基于编辑器的安装。

1. 作为 [文件系统所有者](../file-system/overview.md)，登录到您的应用程序服务器。

1. 转到Web服务器docroot目录或您已配置为虚拟主机docroot的目录。 在本例中，我们使用Ubuntu默认值 `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. 全局安装编辑器。 在安装Adobe Commerce之前，需要编辑器更新依赖项：

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. 使用Adobe Commerce中继资料创建编辑器项目。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出现提示时，输入 [身份验证密钥](../authentication-keys.md). 您的 _公钥_ 是您的用户名；您的 _私钥_ 是您的密码。

1. 在安装应用程序之前，为Web服务器组设置读写权限。 这是必要的，以便命令行可以将文件写入文件系统。

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. 从安装 [命令行](../../advanced.md). 此示例假定安装目录名为 `magento2ee`， `db-host` 在同一台计算机上(`localhost`)，并且 `db-name`， `db-user`、和 `db-password` 全部 `magento`：

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. 切换到开发人员模式：

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### 配置nginx

我们建议使用 `nginx.conf.sample` 安装目录和nginx虚拟主机中提供的配置文件。

这些说明假定您使用的是nginx虚拟主机的Ubuntu默认位置(例如， `/etc/nginx/sites-available`)和Ubuntu默认docroot(例如， `/var/www/html`)但是，您可以更改这些位置以适合您的环境。

1. 为您的站点创建新的虚拟主机：

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. 添加以下配置：

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >此 `include` 指令必须指向安装目录中的示例nginx配置文件。

1. 替换 `www.magento-dev.com` 使用您的域名。 此名称必须匹配您在安装Adobe Commerce时指定的基本URL。

1. 保存并退出编辑器。

1. 通过在中创建指向新创建的虚拟主机的符号链接来激活该虚拟主机 `/etc/nginx/sites-enabled` 目录：

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. 验证语法是否正确：

   ```bash
   nginx -t
   ```

1. 重新启动nginx：

   ```bash
   systemctl restart nginx
   ```

### 验证安装

打开Web浏览器，然后导航到您站点的基本URL，以访问 [验证安装](../../next-steps/verify.md).

## CentOS 7

以下部分介绍了如何使用nginx、PHP和MySQL在CentOS 7上安装Adobe Commerce 2.x。

### 安装nginx

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

安装完成后，启动nginx并将其配置为在引导时启动：

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

完成以下部分并安装应用程序后，我们将使用示例配置文件来配置nginx。

### 安装和配置php-fpm

Adobe Commerce需要多个 [PHP](../php-settings.md) 扩展才能正常运行。 除了这些扩展之外，您还必须安装和配置 `php-fpm` 扩展名来表示您使用的是nginx。

1. 安装 `php-fpm`：

   ```bash
   yum -y install php70w-fpm
   ```

1. 打开 `/etc/php.ini` 文件中的文件。

1. 取消注释 `cgi.fix_pathinfo` 行并将值更改为 `0`.

1. 编辑文件以匹配以下行：

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >测试Adobe Commerce时，我们建议将内存限制设置为2 G。 请参阅 [必需的PHP设置](../php-settings.md) 以了解更多信息。

1. 取消注释会话路径目录并设置路径：

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. 保存并退出编辑器。

1. 打开 `/etc/php-fpm.d/www.conf` 在编辑器中。

1. 编辑文件以匹配以下行：

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. 取消对环境行的注释：

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. 保存并退出编辑器。

1. 为PHP会话路径创建一个目录，并将所有者更改为 `apache` 用户和组：

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. 为PHP会话路径创建一个目录，并将所有者更改为 `apache` 用户和组：

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. 启动 `php-fpm` 服务并将其配置为在引导时启动：

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. 验证 `php-fpm` 服务正在运行：

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### 安装和配置MySQL

请参阅 [MySQL](..//database/mysql.md) 以了解更多信息。

### 安装和配置

有多种下载Adobe Commerce的方法，包括：

* [获取Composer隐含](../../composer.md)

* [克隆Git存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

此示例显示了使用命令行进行的基于编辑器的安装。

1. 作为 [文件系统所有者](../file-system/overview.md)，登录到您的应用程序服务器。

1. 转到Web服务器docroot目录或您已配置为虚拟主机docroot的目录。 在本例中，我们使用Ubuntu默认值 `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. 全局安装编辑器。 在安装Adobe Commerce之前，需要编辑器更新依赖项：

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. 使用Adobe Commerce中继资料创建编辑器项目。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出现提示时，输入 [身份验证密钥](../authentication-keys.md). 您的 _公钥_ 是您的用户名；您的 _私钥_ 是您的密码。

1. 在安装应用程序之前，为Web服务器组设置读写权限。 这是必要的，以便命令行可以将文件写入文件系统。

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. 从安装 [命令行](../../advanced.md). 此示例假定安装目录名为 `magento2ee`， `db-host` 在同一台计算机上(`localhost`)，并且 `db-name`， `db-user`、和 `db-password` 全部 `magento`：

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. 切换到开发人员模式：

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### 配置nginx

我们建议使用 `nginx.conf.sample` 安装目录和nginx虚拟主机中提供的配置文件。

这些说明假定您正在使用nginx虚拟主机的CentOS默认位置(例如， `/etc/nginx/conf.d`)和默认docroot(例如， `/usr/share/nginx/html`)但是，您可以更改这些位置以适合您的环境。

1. 为您的站点创建新的虚拟主机：

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. 添加以下配置：

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >此 `include` 指令必须指向安装目录中的示例nginx配置文件。

1. 替换 `www.magento-dev.com` 使用您的域名。

1. 保存并退出编辑器。

1. 验证语法是否正确：

   ```bash
   nginx -t
   ```

1. 重新启动nginx：

   ```bash
   systemctl restart nginx
   ```

### 配置SELinux和Firewald

在CentOS 7上，SELinux默认处于启用状态。 使用以下命令查看它是否正在运行：

```bash
sestatus
```

要配置SELinux和firewald：

1. 安装SELinux管理工具：

   ```bash
   yum -y install policycoreutils-python
   ```

1. 运行以下命令以更改安装目录的安全上下文：

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. 安装防火墙包：

   ```bash
   yum -y install firewalld
   ```

1. 启动防火墙服务并将其配置为在引导时启动：

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. 运行以下命令以打开HTTP和HTTPS端口，以便您可以从Web浏览器访问基本URL：

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### 验证安装

打开Web浏览器，然后导航到您站点的基本URL，以访问 [验证安装](../../next-steps/verify.md).
