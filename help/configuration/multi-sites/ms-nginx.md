---
title: 使用Nginx设置多个网站
description: 按照本教程使用Nginx设置多个网站。
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# 使用Nginx设置多个网站

我们假定：

- 您正在使用开发计算机（笔记本电脑、虚拟机或类似设备）。

   在托管环境中部署多个网站可能需要执行其他任务；有关更多信息，请与您的托管提供商联系。

   在云基础架构上设置Adobe Commerce需要执行其他任务。 完成本主题中讨论的任务后，请参阅 [设置多个网站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _云基础架构上的Commerce指南_.

- 在一个虚拟主机文件中接受多个域或为每个网站使用一个虚拟主机；虚拟主机配置文件位于 `/etc/nginx/sites-available`.
- 您使用 `nginx.conf.sample` 由Commerce提供，仅包含本教程中讨论的修改。
- Commerce软件安装在 `/var/www/html/magento2`.
- 除默认网站外，您还有两个网站：

   - `french.mysite.mg` 带有网站代码 `french` 和存储视图代码 `fr`
   - `german.mysite.mg` 带有网站代码 `german` 和存储视图代码 `de`
   - `mysite.mg` 是默认网站和默认商店视图

>[!TIP]
>
>请参阅 [创建网站](ms-admin.md#step-2-create-websites) 和 [创建商店视图](ms-admin.md#step-4-create-store-views) 以获取有关查找这些值的帮助。

以下是使用nginx设置多个网站的路线图：

1. [设置网站、商店和商店视图](ms-admin.md) 在Admin中。
1. 创建 [Nginx虚拟主机](#step-2-create-nginx-virtual-hosts))以映射多个网站或每个Commerce网站的一个Nginx虚拟主机（具体步骤详见下文）。
1. 传递以下项的值： [图像变量](ms-overview.md) `$MAGE_RUN_TYPE` 和 `$MAGE_RUN_CODE` 使用Magento提供的 `nginx.conf.sample` （步骤详见下文）。

   - `$MAGE_RUN_TYPE` 可以是 `store` 或 `website`：

      - 使用 `website` 在您的店面中加载您的网站。
      - 使用 `store` 以加载您店面中的任何商店视图。
   - `$MAGE_RUN_CODE` 是与对应的独特网站或商店视图代码 `$MAGE_RUN_TYPE`.


1. 在Commerce管理员中更新基本URL配置。

## 步骤1：在“管理员”中创建网站、商店和存储视图

参见 [在“管理员”中设置多个网站、商店和商店视图](ms-admin.md).

## 步骤2：创建nginx虚拟主机

此步骤讨论如何在店面中加载网站。 您可以使用网站或商店视图；如果使用商店视图，则必须相应地调整参数值。 您必须以用户身份完成此部分中的任务， `sudo` 权限。

只使用一个 [nginx虚拟主机文件](#step-2-create-nginx-virtual-hosts)，可保持简洁nginx配置。 通过使用多个虚拟主机文件，您可以自定义每个存储区(以便使用自定义位置 `french.mysite.mg` 例如)。

**创建一个虚拟主机** （简化）：

此配置将扩展 [nginx配置](../../installation/prerequisites/web-server/nginx.md).

1. 打开文本编辑器，并将以下内容添加到名为的新文件中 `/etc/nginx/sites-available/magento`：

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

1. 将更改保存到文件并退出文本编辑器。
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

有关map指令的更多详细信息，请参见 [有关map指令的nginx文档](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**创建多个虚拟主机**：

1. 打开文本编辑器，并将以下内容添加到名为的新文件中 `/etc/nginx/sites-available/french.mysite.mg`：

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

1. 创建另一个名为的文件 `german.mysite.mg` 在同一目录中，包含以下内容：

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

1. 将更改保存到文件并退出文本编辑器。
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

## 步骤3：修改nginx.conf.sample

>[!TIP]
>
>不要编辑 `nginx.conf.sample` 文件；它是一个核心Commerce文件，可随每个新版本更新。 相反，请复制 `nginx.conf.sample` 重命名该文件，然后编辑复制的文件。

**编辑主应用程序的PHP入口点**：

要修改 `nginx.conf.sample` 文件**：

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

1. 更新 `nginx.conf.sample` 文件，在include语句前具有以下两行：

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

更新了主应用程序的PHP入口点的示例如下所示：

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

## 步骤4：更新基本URL配置

您必须更新基本URL `french` 和 `german` Commerce管理员中的网站。

### 更新法语网站基本URL

1. 登录到Commerce管理员并导航到 **商店** > **设置** > **配置** > **常规** > **Web**.
1. 更改 _配置范围_ 到 `french` 网站。
1. 展开 **基本URL** 部分并更新 **基本URL** 和 **基本链接URL** 值至 `http://french.magento24.com/`.
1. 展开 **基本URL（安全）** 部分并更新 **安全基本URL** 和 **安全基本链接URL** 值至 `https://french.magento24.com/`.
1. 单击 **保存配置** 并保存配置更改。

### 更新德语网站基本URL

1. 登录到Commerce管理员并导航到 **商店** > **设置** > **配置** > **常规** > **Web**.
1. 更改 _配置范围_ 到 `german` 网站。
1. 展开 **基本URL** 部分并更新 **基本URL** 和 **基本链接URL** 值至 `http://german.magento24.com/`.
1. 展开 **基本URL（安全）** 部分并更新 **安全基本URL** 和 **安全基本链接URL** 值至 `https://german.magento24.com/`.
1. 单击 **保存配置** 并保存配置更改。

### 清理缓存

运行以下命令以清理 `config` 和 `full_page` 缓存。

```bash
bin/magento cache:clean config full_page
```

## 验证您的站点

除非您已经为商店的URL设置了DNS，否则您必须向中的主机添加一条静态路由 `hosts` 文件：

1. 找到您的操作系统 `hosts` 文件。
1. 采用以下格式添加静态路由：

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. 在浏览器中转到以下URL之一：

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 在托管环境中部署多个网站可能需要执行其他任务；有关更多信息，请与您的托管提供商联系。
>- 在云基础架构上设置Adobe Commerce需要执行其他任务；请参阅 [设置多个云网站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _云基础架构上的Commerce指南_.


### 疑难解答

- 如果您的法语和德语站点返回404但您的管理员加载了，请确保您已完成 [步骤6：将存储代码添加到基本URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- 如果所有URL都返回404，请确保已重新启动Web服务器。
- 如果管理员无法正常工作，请确保正确设置虚拟主机。
