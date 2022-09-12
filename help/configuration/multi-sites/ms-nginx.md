---
title: 使用Nginx设置多个网站
description: 请按照本教程使用Nginx设置多个网站。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---


# 使用Nginx设置多个网站

我们假定：

- 您正在使用开发计算机（笔记本电脑、虚拟机或类似设备）。

   在托管环境中部署多个网站可能需要执行其他任务；有关更多信息，请咨询您的托管提供商。

   在云基础架构上设置Adobe Commerce时需要执行其他任务。 完成本主题中讨论的任务后，请参阅 [设置多个网站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html) 在 _Commerce Cloud指南_.

- 在一个虚拟主机文件中接受多个域，或在每个网站中使用一个虚拟主机；虚拟主机配置文件位于 `/etc/nginx/sites-available`.
- 您使用 `nginx.conf.sample` 由商务提供，且仅包含本教程中讨论的修改。
- 商务软件安装在 `/var/www/html/magento2`.
- 您有两个网站（默认网站除外）：

   - `french.mysite.mg` 使用网站代码 `french` 和存储视图代码 `fr`
   - `german.mysite.mg` 使用网站代码 `german` 和存储视图代码 `de`
   - `mysite.mg` 是默认网站和默认商店视图

>[!TIP]
>
>请参阅 [创建网站](ms-admin.md#step-2-create-websites) 和 [创建商店视图](ms-admin.md#step-4-create-store-views) 以帮助查找这些值。

以下是使用Nix设置多个网站的路线图：

1. [设置网站、商店和商店视图](ms-admin.md) 中。
1. 创建 [Nginx虚拟主机](#step-2-create-nginx-virtual-hosts))以映射多个网站或每个商务网站的一个Nginx虚拟主机（详见下文步骤）。
1. 传递 [MAGE变量](ms-overview.md) `$MAGE_RUN_TYPE` 和 `$MAGE_RUN_CODE` 到nginx，使用Magento提供 `nginx.conf.sample` （详细步骤如下）。

   - `$MAGE_RUN_TYPE` 可以是 `store` 或 `website`:

      - 使用 `website` 来加载您的网站。
      - 使用 `store` 来加载店面中的任何商店视图。
   - `$MAGE_RUN_CODE` 是与 `$MAGE_RUN_TYPE`.


1. 在商务管理员中更新基本URL配置。

## 步骤1:在“管理员”中创建、存储和存储视图

请参阅 [在管理员中设置多个网站、商店和存储视图](ms-admin.md).

## 步骤2:创建原始虚拟主机

此步骤讨论如何在 [店面](https://glossary.magento.com/storefront). 您可以使用网站或存储视图；如果使用商店视图，则必须相应地调整参数值。 您必须以用户身份通过 `sudo` 权限。

只需使用一个 [nginx虚拟主机文件](#step-2-create-nginx-virtual-hosts)，则可以使nginx配置简单而干净。 通过使用多个虚拟主机文件，您可以自定义每个存储(以使用 `french.mysite.mg` 例如)。

**创建一个虚拟主机** （简化）：

此配置在 [nginx配置](../../installation/prerequisites/web-server/nginx.md).

1. 打开文本编辑器，并将以下内容添加到名为的新文件 `/etc/nginx/sites-available/magento`:

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 保存对文件所做的更改并退出文本编辑器。
1. 验证服务器配置：

   ```bash
   nginx -t
   ```

1. 如果成功，将显示以下消息：

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果显示错误，请检查虚拟主机配置文件的语法。

1. 在中创建符号链接 `/etc/nginx/sites-enabled` 目录：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

有关map指令的更多详细信息，请参阅 [map指令的nginx文档](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**创建多个虚拟主机**:

1. 打开文本编辑器，并将以下内容添加到名为的新文件 `/etc/nginx/sites-available/french.mysite.mg`:

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 创建另一个名为 `german.mysite.mg` 在同一目录中，包含以下内容：

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 保存对文件所做的更改并退出文本编辑器。
1. 验证服务器配置：

   ```bash
   nginx -t
   ```

1. 如果成功，将显示以下消息：

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果显示错误，请检查虚拟主机配置文件的语法。

1. 在中创建符号链接 `/etc/nginx/sites-enabled` 目录：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## 步骤3:修改nginx.conf.sample

>[!TIP]
>
>请勿编辑 `nginx.conf.sample` 文件；它是一个核心Commerce文件，可随每个新版本一起更新。 而是复制 `nginx.conf.sample` 文件，重命名该文件，然后编辑复制的文件。

**编辑主应用程序的PHP入口点**:

修改 `nginx.conf.sample` 文件**:

1. 打开文本编辑器并查看 `nginx.conf.sample` 文件，`<magento2_installation_directory>/nginx.conf.sample`. 查找以下部分：

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. 更新 `nginx.conf.sample` 文件，其中包含以下两行：

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

主应用程序的更新PHP入口点示例如下所示：

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## 步骤4:更新基本URL配置

您必须更新 `french` 和 `german` 网站。

### 更新法语网站基本URL

1. 登录到Commerce管理员，然后导航到 **商店** > **设置** > **配置** > **常规** > **Web**.
1. 更改 _配置范围_ 到 `french` 网站。
1. 展开 **基本URL** 部分和更新 **基本URL** 和 **基本链接URL** 值 `http://french.magento24.com/`.
1. 展开 **基本URL（安全）** 部分和更新 **安全基本URL** 和 **安全基本链接URL** 值 `https://french.magento24.com/`.
1. 单击 **保存配置** 并保存配置更改。

### 更新德国网站基本URL

1. 登录到Commerce管理员，然后导航到 **商店** > **设置** > **配置** > **常规** > **Web**.
1. 更改 _配置范围_ 到 `german` 网站。
1. 展开 **基本URL** 部分和更新 **基本URL** 和 **基本链接URL** 值 `http://german.magento24.com/`.
1. 展开 **基本URL（安全）** 部分和更新 **安全基本URL** 和 **安全基本链接URL** 值 `https://german.magento24.com/`.
1. 单击 **保存配置** 并保存配置更改。

### 清除缓存

运行以下命令以清除 `config` 和 `full_page` 缓存。

```bash
bin/magento cache:clean config full_page
```

## 验证您的网站

除非您为商店的URL设置了DNS，否则您必须在 `hosts` 文件：

1. 找到您的操作系统 `hosts` 文件。
1. 以下格式添加静态路由：

   ```conf
   <ip address> french.mysite.mg
   <ip address> german.mysite.mg
   ```

1. 在浏览器中转到以下URL之一：

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 在托管环境中部署多个网站可能需要执行其他任务；有关更多信息，请咨询您的托管提供商。
>- 在云基础架构上设置Adobe Commerce需要执行其他任务；请参阅 [设置多个云网站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html) 在 _Commerce Cloud指南_.


### 疑难解答

- 如果您的法语和德语网站返回404秒，但加载了管理员，请确保您已完成 [步骤6:将存储代码添加到基本URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- 如果所有URL都返回404，请确保重新启动Web服务器。
- 如果管理员无法正常运行，请确保正确设置虚拟主机。
