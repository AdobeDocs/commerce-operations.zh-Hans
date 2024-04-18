---
title: 修改docroot以提高安全性
description: 防止对Adobe Commerce本地文件系统的未经授权的基于浏览器的访问。
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# 修改docroot以提高安全性

在使用Apache Web Server进行的标准安装中，Adobe Commerce安装到默认的Web根目录： `/var/www/html/magento2`.

此 `magento2/` 目录包含以下内容：

- `pub/`
- `setup/`
- `var/`

应用程序服务源自 `/var/www/html/magento2/pub`. 由于可从浏览器访问，因此文件系统的其余部分易受攻击。
将webroot设置为 `pub/` 目录阻止站点访客从浏览器访问文件系统的敏感区域。

本主题介绍如何更改现有实例上的Apache docroot以从提供文件 `pub/` 目录，这样更加安全。

## 关于nginx的说明

如果您使用 [恩金克斯](../prerequisites/web-server/nginx.md) 和 [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 文件包含在安装目录中，您可能已经从 `pub/` 目录。

在用于定义站点的服务器块中时， `nginx.conf.sample` 配置将覆盖服务器的docroot设置，以便从提供文件 `pub/` 目录。 例如，请参见以下配置中的最后一行：

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

要完成本教程，您需要访问在LAMP栈栈上运行的工作安装：

- Linux
- Apache (2.4+)
- MySQL （5.7及更高版本）
- PHP (7.4)
- Elasticsearch(7.x)或OpenSearch (1.2)
- Adobe Commerce (2.4+)

>[!NOTE]
>
>请参阅 [先决条件](../prerequisites/overview.md) 和 [安装指南](../overview.md) 以了解更多信息。

## 1.编辑服务器配置

虚拟主机文件的名称和位置取决于您运行的Apache版本。 此示例显示了Apache v2.4上虚拟主机文件的名称和位置。

1. 登录到应用程序服务器。
1. 编辑您的虚拟主机文件：

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. 将路径添加到 `pub/` 目录到 `DocumentRoot` 指令：

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

1. 重新启动Apache：

   ```bash
   systemctl restart apache2
   ```

## 2.更新您的基本URL

如果在服务器的主机名或IP地址后附加目录名称，则可在安装应用程序时创建基本URL(例如 `http://192.168.33.10/magento2`)，您需要将其删除。

>[!NOTE]
>
>替换 `192.168.33.10` 使用服务器的主机名。

1. 登录到数据库：

   ```bash
   mysql -u <user> -p
   ```

1. 指定安装应用程序时创建的数据库：

   ```shell
   use <database-name>
   ```

1. 更新基本URL：

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3.更新环境文件php

将以下节点附加到 `env.php` 文件。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

请参阅 [env.php参考](../../configuration/reference/config-reference-envphp.md) 以了解更多信息。

## 4.切换模式

[应用程序模式](../../configuration/bootstrap/application-modes.md)，其中包括 `production` 和 `developer`，旨在提高安全性并使开发更轻松。 根据名字的指示，您应切换到 `developer` 扩展或自定义应用程序时模式并切换到 `production` 模式。

在模式之间切换是验证服务器配置是否正常运行的重要步骤。 您可以使用CLI工具在模式之间切换：

1. 转到安装目录。
1. 切换到 `production` 模式。

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 刷新浏览器并验证店面是否正确显示。
1. 切换到 `developer` 模式。

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. 刷新浏览器并验证店面是否正确显示。

## 5.验证店面

在Web浏览器中转到店面以验证一切正常。

1. 打开Web浏览器，并在地址栏中输入服务器的主机名或IP地址。 例如， `http://192.168.33.10`.

   下图显示了一个店面页面的示例。 如果它显示如下，则表示您的安装成功！

   ![验证安装成功的店面](../../assets/installation/install-success_store.png)

   请参阅 [疑难解答部分](https://support.magento.com/hc/en-us/articles/360032994352) 页面显示404（未找到）或无法加载图像、CSS和JS等其他资产。

1. 尝试从浏览器访问应用程序目录。 在地址栏中将目录名称附加到服务器的主机名或IP地址：

   如果您看到404或“访问被拒绝”消息，则表示您已成功限制对文件系统的访问。

   ![访问被拒绝](../../assets/installation/access-denied.png)
