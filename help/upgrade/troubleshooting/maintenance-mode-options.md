---
title: 升级的维护模式选项
description: 创建自定义维护模式页面，在您执行升级时，您的客户将在Adobe Commerce或Magento Open Source店面上看到该页面。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# 升级的维护模式选项

本主题讨论如何在升级Magento应用程序时创建向用户显示的自定义维护页面。 创建自定义页面是可选的，但是建议您创建此页面，因为您的网站在升级过程中可以访问。

创建自定义页面以将用户重定向到该页面，会阻止用户访问该网站，并通知用户该网站正在进行维护。

>[!NOTE]
>
>您必须以用户身份执行此部分中的任务， `root` 权限。 在开发人员模式下，无法设置自定义维护页面。

## 创建自定义维护页面

要创建维护页面并将其重定向到该页面，请首先创建一个名为的维护页面：

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

添加以下内容：

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Apache的“自定义维护”页

本节将讨论如何创建自定义维护页面以及如何将流量重定向到该页面。

此部分中的示例展示了如何修改以下文件，这是设置维护页面的一种方法：

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` （乌本图）、 `/etc/httpd/conf/httpd.conf` (CentOS)

要将流量重定向到自定义维护页面，请执行以下操作：

1. 更新Apache配置以执行以下操作：

   - 将所有流量重定向到维护页面
   - 允许列表管理某些IP，以便管理员可以升级Magento软件。

   以下示允许列表例于192.0.2.110。

   在Apache配置文件的末尾添加以下内容：

   ```terminal
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. 重新启动Apache:

   - CentOS: `service httpd restart`
   - 乌本图： `service apache2 restart`

1. 输入以下命令：

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [升级系统](../implementation/perform-upgrade.md).
1. 测试您的网站以确保其正常运行。
1. 升级完成后，删除 `maintenance.enable`.

## nginx的自定义维护页面

本节将讨论如何创建自定义维护页面以及如何将流量重定向到该页面。

要将流量重定向到自定义维护页面，请执行以下操作：

1. 使用文本编辑器打开包含服务器块的初始配置文件。
1. 将以下内容添加到服务器块(`server` 仅为清晰起见而显示；不添加第二个服务器块)。

   以下允许列表在安装Magento的系统上的IP地址192.0.2.110和192.0.2.115 `/var/www/html/magento2`:

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 输入以下命令：

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. 重新加载初始配置：

   ```bash
   service nginx reload
   ```

1. [升级系统](../implementation/perform-upgrade.md).
1. 测试您的网站以确保其正常运行。
1. 升级完成后，删除或重命名 `maintenance.enable`
1. 重新加载初始配置：

   ```bash
   service nginx reload
   ```
