---
title: 修改docroot以提高安全性
description: 防止未经授权的基于浏览器的访问Adobe Commerce或Magento Open Source本地文件系统。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# 修改docroot以提高安全性

在使用Apache Web服务器的标准安装中，Adobe Commerce和Magento Open Source安装到默认Web根目录： `/var/www/html/magento2`.

的 `magento2/` 目录包含以下内容：

- `pub/`
- `setup/`
- `var/`

应用程序的提供方 `/var/www/html/magento2/pub`. 文件系统的其余部分易受攻击，因为它可以从浏览器访问。
将webroot设置为 `pub/` 目录阻止站点访客从浏览器访问文件系统的敏感区域。

本主题介绍如何更改现有实例上的Apache Docroot，以从 `pub/` 目录的安全性。

## 关于nginx的注释

如果您使用 [nginx](../prerequisites/web-server/nginx.md) 和 [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 文件，则您可能已在从 `pub/` 目录访问Advertising Cloud的帮助。

在定义网站的服务器块中使用时， `nginx.conf.sample` 配置将覆盖服务器的docroot设置，以从 `pub/` 目录访问Advertising Cloud的帮助。 例如，请参阅以下配置中的最后一行：

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## 开始之前

要完成本教程，您需要访问 [灯](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) 堆栈：

- Linux
- Apache(2.4+)
- MySQL(5.7+)
- PHP(7.4)
- Elasticsearch(7.x)或OpenSearch(1.2)
- Adobe Commerce或Magento Open Source(2.4+)

>[!NOTE]
>
>请参阅 [先决条件](../prerequisites/overview.md) 和 [安装指南](../overview.md) 以了解更多信息。

## 1.编辑服务器配置

虚拟主机文件的名称和位置取决于您运行的Apache版本。 此示例显示Apache v2.4上虚拟主机文件的名称和位置。

1. 登录到应用程序服务器。
1. 编辑虚拟主机文件：

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. 将路径添加到 `pub/` 目录 `DocumentRoot` 指令：

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. 重新启动Apache:

   ```bash
   systemctl restart apache2
   ```

## 2.更新基本URL

如果在安装应用程序时将目录名称附加到服务器的主机名或IP地址，以创建基本URL(例如 `http://192.168.33.10/magento2`)，则需要将其删除。

>[!NOTE]
>
>替换 `192.168.33.10` 和您服务器的主机名。

1. 登录数据库：

   ```bash
   mysql -u <user> -p
   ```

1. 指定在安装应用程序时创建的数据库：

   ```shell
   use <database-name>
   ```

1. 更新基本URL:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3.更新env.php文件

将以下节点附加到 `env.php` 文件。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

请参阅 [env.php引用](../../configuration/reference/config-reference-envphp.md) 以了解更多信息。

## 4.切换模式

[应用模式](../../configuration/bootstrap/application-modes.md)，其中包括 `production` 和 `developer`，旨在提高安全性并简化开发。 如名称所示，您应切换到 `developer` 模式(扩展或自定义应用程序并切换到 `production` 模式。

在模式之间切换是验证服务器配置是否正常工作的重要步骤。 可以使用CLI工具在不同模式之间切换：

1. 转到安装目录。
1. 切换到 `production` 模式。

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 刷新浏览器并验证店面是否显示正确。
1. 切换到 `developer` 模式。

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 刷新浏览器并验证店面是否显示正确。

## 5.验证店面

转到 [店面](https://glossary.magento.com/storefront) 来验证一切是否正常。

1. 打开Web浏览器，然后在地址栏中输入服务器的主机名或IP地址。 例如， `http://192.168.33.10`.

   下图显示了一个示例店面页面。 如果按如下方式显示，则表明安装成功！

   ![用于验证安装是否成功的店面](../../assets/installation/install-success_store.png)

   请参阅 [疑难解答部分](https://support.magento.com/hc/en-us/articles/360032994352) 如果页面显示404（未找到）或加载图像、CSS和JS等其他资产失败。

1. 尝试从浏览器访问应用程序目录。 将目录名称附加到地址栏中服务器的主机名或IP地址：

   如果您看到404或“拒绝访问”消息，则表示您已成功限制对文件系统的访问。

   ![拒绝访问](../../assets/installation/access-denied.png)
