---
title: 升级的维护模式选项
description: 创建自定义维护模式页面，以便客户在执行升级时在Adobe Commerce店面中看到该页面。
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# 用于升级的维护模式选项

本主题讨论如何创建自定义维护页，以便在升级Magento应用程序时向用户显示。 创建自定义页面是可选的，但建议创建自定义页面，因为您的网站在升级过程中可访问。

创建一个自定义页面，用户将重定向到该页面，这会阻止对该网站的任何访问，并会通知用户该网站正在进行维护。

>[!NOTE]
>
>您必须以用户身份执行本节中的任务， `root` 权限。 在开发人员模式下无法设置自定义维护页面。

## 创建自定义维护页面

要创建维护页面并重定向到该页面，请首先创建一个名为的维护页面：

- Apache： `<web server docroot>/maintenance.html`
- 恩金克斯： `<magento_root>/maintenance.html`

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

## Apache的自定义维护页面

此部分讨论如何创建自定义维护页面以及如何将流量重定向到该页面。

此部分中的示例说明如何修改以下文件，这是设置维护页面的一种方法：

- Apache 2.4： `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2： `/etc/apache2/sites-available/default` (Ubuntu)， `/etc/httpd/conf/httpd.conf` (CentOS)

要将流量重定向到自定义维护页面，请执行以下操作：

1. 更新Apache配置以执行以下操作：

   - 将所有流量重定向到维护页面
   - 允许列表特定IP，以便管理员可以升级Magento软件。

   以下示例列入允许列表192.0.2.110。

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

1. 重新启动Apache：

   - CentOS： `service httpd restart`
   - Ubuntu： `service apache2 restart`

1. 输入以下命令：

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [升级您的系统](../implementation/perform-upgrade.md).
1. 测试您的网站以确保其正常运行。
1. 升级完成后，删除 `maintenance.enable`.

## nginx的自定义维护页面

此部分讨论如何创建自定义维护页面以及如何将流量重定向到该页面。

要将流量重定向到自定义维护页面，请执行以下操作：

1. 使用文本编辑器打开包含服务器块的nginx配置文件。
1. 将以下内容添加到服务器块(`server` 仅为了清楚起见而显示；不要添加第二个服务器块)。

   以下允许列表在安装了Magento的系统上IP地址192.0.2.110和192.0.2.115 `/var/www/html/magento2`：

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

1. 重新加载nginx配置：

   ```bash
   service nginx reload
   ```

1. [升级您的系统](../implementation/perform-upgrade.md).
1. 测试您的网站以确保其正常运行。
1. 升级完成后，删除或重命名 `maintenance.enable`
1. 重新加载nginx配置：

   ```bash
   service nginx reload
   ```
