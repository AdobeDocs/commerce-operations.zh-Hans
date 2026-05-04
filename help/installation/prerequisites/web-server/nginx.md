---
title: 为内部部署安装Nginx
description: 了解如何为本地Adobe Commerce部署安装和配置Nginx Web服务器。 设置PHP-FPM和虚拟主机。
feature: Install, Configuration
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hans/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1477'
ht-degree: 0%

---

# 为内部部署安装Nginx {#nginx}

本指南将指导您完成为Adobe Commerce内部部署安装Nginx以及配置Commerce所需的Nginx设置。 其中包括针对Ubuntu和CentOS的特定于操作系统的过程，以及配置PHP-FPM的指南。 Adobe建议遵循本指南中提供的配置说明，以保留Commerce应用程序的功能和安全性。

Adobe支持您的Adobe Commerce版本的[系统要求](../../system-requirements.md)中列出的Nginx版本。 支持的版本因版本而异。 Nginx还需要支持的PHP-FPM配置。 有关相关的PHP要求，请参阅[PHP](../php-settings.md)。

## 在Ubuntu上安装

使用本节在Ubuntu上通过Nginx、PHP和MySQL安装Adobe Commerce。

### 安装Nginx

```shell
sudo apt -y install nginx
```

您也可以[从源](https://www.armanism.com/blog/install-nginx-on-ubuntu)构建Nginx。

完成以下部分并安装应用程序后，请使用示例配置文件来[配置Nginx](#configure-nginx)。 此推荐的配置保留了Commerce应用程序的功能和安全性。

### 安装和配置PHP-FPM

Adobe Commerce需要多个[PHP扩展](../php-settings.md)才能正常运行。 除了这些扩展之外，如果您使用Nginx，则还必须安装和配置`php-fpm`扩展。

要安装和配置`php-fpm`，请执行以下操作：

1. 安装Adobe Commerce版本支持的PHP版本的`php-fpm`和`php-cli`包。 在Ubuntu上，包名称通常遵循以下模式：

   ```shell
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >将`<php-version>`替换为您正在安装的Adobe Commerce版本的[系统要求](../../system-requirements.md)中列出的受支持的PHP次要版本。 在以下步骤中，在文件路径、服务名称和套接字路径中使用相同的值。

1. 在编辑器中打开`php.ini`文件：

   ```shell
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```shell
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. 编辑这两个文件以匹配以下行：

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe建议在测试Adobe Commerce时将内存限制设置为2 GB。 有关详细信息，请参阅[必需的PHP设置](../php-settings.md)。

1. 保存并退出编辑器。

1. 重新启动`php-fpm`服务：

   ```shell
   systemctl restart php<php-version>-fpm
   ```

### 安装和配置MySQL

有关详细信息，请参阅[MySQL](../database/mysql.md)。

### 安装Adobe Commerce

您可以通过多种方式下载Adobe Commerce：

* [获取Composer隐含](../../composer.md)

* [克隆Git存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

此示例显示了使用命令行进行的基于编辑器的安装。

1. 以[文件系统所有者](../file-system/overview.md)的身份登录到您的应用程序服务器。

1. 转到Web服务器docroot目录或您已配置为虚拟主机docroot的目录。 在此示例中，我们使用Ubuntu默认`/var/www/html`。

   ```shell
   cd /var/www/html
   ```

1. 全局安装编辑器。 在安装Adobe Commerce之前，需要编辑器更新依赖项：

   ```shell
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. 使用Adobe Commerce中继资料创建编辑器项目。

   **Magento Open Source**

   ```shell
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```shell
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出现提示时，输入您的[身份验证密钥](../authentication-keys.md)。 您的&#x200B;_公钥_&#x200B;是您的用户名；_私钥_&#x200B;是您的密码。

1. 在安装应用程序之前，为Web服务器组设置读写权限。 这是必要的，以便命令行可以将文件写入文件系统。

   ```shell
   cd /var/www/html/<magento install directory>
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```shell
   chown -R :www-data . # Ubuntu
   ```

   ```shell
   chmod u+x bin/magento
   ```

1. 从[命令行](../../advanced.md)安装。 此示例假定安装目录名为`magento2ee`，并且数据库主机位于同一台计算机(`localhost`)上：

   ```shell
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >使用`--search-engine`值和要安装的Adobe Commerce版本所需匹配的主机/端口选项。 对于低于2.4.6的版本，请将`elasticsearch7`与Elasticsearch 7或OpenSearch的`--elasticsearch-*`选项一起使用。 对于版本2.4.6及更高版本，请使用该版本支持的搜索引擎值和相应的CLI选项。

1. 切换到开发人员模式：

   ```shell
   cd /var/www/html/magento2/bin
   ```

   ```shell
   ./magento deploy:mode:set developer
   ```

### 配置Nginx

Adobe建议使用安装目录中提供的`nginx.conf.sample`配置文件和Nginx虚拟主机配置来配置Nginx，以保留Commerce应用程序的功能和安全性。

>[!IMPORTANT]
>
>`nginx.conf.sample`文件提供了所需的应用程序路由以及安全增强规则。 例如，它限制上传到服务器的有害脚本的执行。 如果您不使用此文件或修改其规则，则您负责在自定义nginx配置中实施等效的安全控件。

这些说明假定您正在使用Nginx虚拟主机的Ubuntu默认位置（如`/etc/nginx/sites-available`）和Ubuntu默认docroot（如`/var/www/html`）。 您可以更改这些位置以适合您的环境。

1. 为您的站点创建新的虚拟主机：

   ```shell
   vim /etc/nginx/sites-available/magento
   ```

1. 添加以下配置：

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
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
   >`include`指令必须指向安装目录中的nginx配置文件示例。

1. 将`www.magento-dev.com`替换为您的域名。 此名称必须匹配您在安装Adobe Commerce时指定的基本URL。

1. 保存并退出编辑器。

1. 通过在`/etc/nginx/sites-enabled`目录中创建指向新创建的虚拟主机的符号链接来激活该虚拟主机：

   ```shell
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. 验证语法是否正确：

   ```shell
   nginx -t
   ```

1. 重新启动Nginx：

   ```shell
   systemctl restart nginx
   ```

### 验证安装

要验证安装，请打开Web浏览器并导航到站点的基本URL。 有关详细信息，请参阅[验证安装](../../next-steps/verify.md)。

## 在CentOS 7上安装

使用本节在CentOS 7（带有Nginx、PHP和MySQL）上安装Adobe Commerce。

### 安装Nginx

```shell
yum -y install epel-release
```

```shell
yum -y install nginx
```

安装完成后，启动nginx并将其配置为在引导时启动：

```shell
systemctl start nginx
```

```shell
systemctl enable nginx
```

完成以下部分并安装应用程序后，请使用示例配置文件来配置Nginx。

### 安装和配置PHP-FPM

Adobe Commerce需要多个[PHP](../php-settings.md)扩展才能正常运行。 除了这些扩展之外，如果您使用Nginx，则还必须安装和配置`php-fpm`扩展。

1. 安装`php-fpm`：

   ```shell
   yum -y install <php-fpm-package>
   ```

1. 在编辑器中打开`/etc/php.ini`文件。

   >[!NOTE]
   >
   >安装为要安装的Adobe Commerce版本支持的PHP版本提供`php-fpm`的包。 软件包名称因存储库和操作系统而异。 请参阅[系统要求](../../system-requirements.md)。

1. 取消注释`cgi.fix_pathinfo`行并将值更改为`0`。

1. 编辑文件以匹配以下行：

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe建议在测试Adobe Commerce时将内存限制设置为2 GB。 有关详细信息，请参阅[必需的PHP设置](../php-settings.md)。

1. 取消注释会话路径目录并设置路径：

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. 保存并退出编辑器。

1. 在编辑器中打开`/etc/php-fpm.d/www.conf`。

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

1. 为PHP会话路径创建一个目录，并将所有者更改为`nginx`用户和组：

   ```shell
   mkdir -p /var/lib/php/session/
   ```

   ```shell
   chown -R nginx:nginx /var/lib/php/
   ```

1. 为PHP-FPM套接字创建一个目录，并将所有者更改为`nginx`用户和组：

   ```shell
   mkdir -p /run/php-fpm/
   ```

   ```shell
   chown -R nginx:nginx /run/php-fpm/
   ```

1. 启动`php-fpm`服务并将其配置为在启动时启动：

   ```shell
   systemctl start php-fpm
   ```

   ```shell
   systemctl enable php-fpm
   ```

1. 验证`php-fpm`服务是否正在运行：

   ```shell
   netstat -pl | grep php-fpm.sock
   ```

### 安装和配置MySQL

有关详细信息，请参阅[MySQL](../database/mysql.md)。

### 安装Adobe Commerce

您可以通过多种方式下载Adobe Commerce：

* [获取Composer隐含](../../composer.md)

* [克隆Git存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

此示例显示了使用命令行进行的基于编辑器的安装。

1. 以[文件系统所有者](../file-system/overview.md)的身份登录到您的应用程序服务器。

1. 转到Web服务器docroot目录或您已配置为虚拟主机docroot的目录。 对于此示例，使用CentOS默认值`/usr/share/nginx/html`。

   ```shell
   cd /usr/share/nginx/html
   ```

1. 全局安装编辑器。 在安装Adobe Commerce之前，需要编辑器更新依赖项：

   ```shell
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. 使用Adobe Commerce中继资料创建编辑器项目。

   **Magento Open Source**

   ```shell
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```shell
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出现提示时，输入您的[身份验证密钥](../authentication-keys.md)。 您的&#x200B;_公钥_&#x200B;是您的用户名；_私钥_&#x200B;是您的密码。

1. 在安装应用程序之前，为Web服务器组设置读写权限。 这是必要的，以便命令行可以将文件写入文件系统。

   ```shell
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```shell
   chown -R :nginx . # CentOS
   ```

   ```shell
   chmod u+x bin/magento
   ```

1. 从[命令行](../../advanced.md)安装。 此示例假定安装目录名为`magento2ee`，并且数据库主机位于同一台计算机(`localhost`)上：

   ```shell
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. 切换到开发人员模式：

   ```shell
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```shell
   ./magento deploy:mode:set developer
   ```

### 配置Nginx

我们建议使用安装目录中的`nginx.conf.sample`文件和Nginx虚拟主机配置来配置Nginx。

>[!IMPORTANT]
>
>`nginx.conf.sample`文件提供了所需的应用程序路由以及安全增强规则。 例如，它限制上传到服务器的有害脚本的执行。 如果您不使用此文件或修改其规则，则您负责在自定义nginx配置中实施等效的安全控件。

这些说明假定您正在使用Nginx虚拟主机的CentOS默认位置（如`/etc/nginx/conf.d`）和默认docroot（如`/usr/share/nginx/html`）。 您可以更改这些位置以适合您的环境。

1. 为您的站点创建新的虚拟主机：

   ```shell
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
   >`include`指令必须指向安装目录中的nginx配置文件示例。

1. 将`www.magento-dev.com`替换为您的域名。

1. 保存并退出编辑器。

1. 验证语法是否正确：

   ```shell
   nginx -t
   ```

1. 重新启动Nginx：

   ```shell
   systemctl restart nginx
   ```

### 配置SELinux和firewalld

在CentOS 7上，SELinux默认处于启用状态。 使用以下命令确认其正在运行：

```shell
sestatus
```

要配置SELinux和firewald：

1. 安装SELinux管理工具：

   ```shell
   yum -y install policycoreutils-python
   ```

1. 运行以下命令以更改安装目录的安全上下文：

   ```shell
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```shell
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```shell
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```shell
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```shell
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. 安装防火墙包：

   ```shell
   yum -y install firewalld
   ```

1. 启动防火墙服务并将其配置为在引导时启动：

   ```shell
   systemctl start firewalld
   ```

   ```shell
   systemctl enable firewalld
   ```

1. 运行以下命令以打开HTTP和HTTPS端口，以便您可以从Web浏览器访问基本URL：

   ```shell
   firewall-cmd --permanent --add-service=http
   ```

   ```shell
   firewall-cmd --permanent --add-service=https
   ```

   ```shell
   firewall-cmd --reload
   ```

### 验证安装

要验证安装，请打开Web浏览器并导航到站点的基本URL。 有关详细信息，请参阅[验证安装](../../next-steps/verify.md)。
