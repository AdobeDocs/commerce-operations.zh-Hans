---
title: 使用Nginx设置多个网站
description: 按照本教程使用Nginx设置多个网站。
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# 使用Nginx设置多个网站

我们假定：

- 您正在使用开发计算机（笔记本电脑、虚拟机或类似设备）。

  在托管环境中部署多个网站可能需要执行其他任务；有关更多信息，请咨询您的托管提供商。

  在云基础架构上设置Adobe Commerce需要执行其他任务。 完成本主题中讨论的任务后，请参阅[Commerce on Cloud Infrastructure指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=zh-Hans)中的&#x200B;_设置多个网站或商店_。

- 在一个虚拟主机文件中接受多个域或为每个网站使用一个虚拟主机；虚拟主机配置文件位于`/etc/nginx/sites-available`中。
- 您仅对本教程中讨论的修改使用了Commerce提供的`nginx.conf.sample`。
- Commerce软件安装在`/var/www/html/magento2`中。
- 您拥有默认网站以外的两个网站：

   - 网站代码为`french.mysite.mg`且商店视图代码为`french`的`fr`
   - 网站代码为`german.mysite.mg`且商店视图代码为`german`的`de`
   - `mysite.mg`是默认网站和默认商店视图

>[!TIP]
>
>有关查找这些值的帮助，请参阅[创建网站](ms-admin.md#step-2-create-websites)和[创建商店视图](ms-admin.md#step-4-create-store-views)。

以下是使用nginx设置多个网站的路线图：

1. [在管理员中设置网站、商店和商店视图](ms-admin.md)。
1. 创建一个[Nginx虚拟主机](#step-2-create-nginx-virtual-hosts))以映射多个网站或每个Commerce网站一个Nginx虚拟主机（详细步骤如下）。
1. 使用Magento提供的[将](ms-overview.md)MAGE变量`$MAGE_RUN_TYPE` `$MAGE_RUN_CODE`和`nginx.conf.sample`的值传递给nginx（详细步骤如下）。

   - `$MAGE_RUN_TYPE`可以是`store`或`website`：

      - 使用`website`在您的店面中加载您的网站。
      - 使用`store`加载店面中的任何商店视图。

   - `$MAGE_RUN_CODE`是与`$MAGE_RUN_TYPE`对应的唯一网站或商店视图代码。

1. 在Commerce管理员中更新基本URL配置。

## 步骤1：在“管理员”中创建网站、商店和存储视图

查看[在Admin](ms-admin.md)中设置多个网站、商店和商店视图。

## 步骤2：创建nginx虚拟主机

此步骤讨论如何在店面中加载网站。 您可以使用网站或商店视图；如果使用商店视图，则必须相应地调整参数值。 您必须以具有`sudo`权限的用户身份完成此部分中的任务。

只需使用一个[nginx虚拟主机文件](#step-2-create-nginx-virtual-hosts)，就可以使nginx配置简单而干净。 通过使用多个虚拟主机文件，您可以自定义每个存储（以便为`french.mysite.mg`实例使用自定义位置）。

**创建一个虚拟主机**（简化）：

此配置扩展到[nginx配置](../../installation/prerequisites/web-server/nginx.md)。

1. 打开文本编辑器，并将以下内容添加到名为`/etc/nginx/sites-available/magento`的新文件中：

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

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果显示错误，请检查虚拟主机配置文件的语法。

1. 在`/etc/nginx/sites-enabled`目录中创建符号链接：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

有关map指令的更多详细信息，请参阅有关map指令[的](http://nginx.org/en/docs/http/ngx_http_map_module.html#map)nginx文档。


**要创建多个虚拟主机**：

1. 打开文本编辑器，并将以下内容添加到名为`/etc/nginx/sites-available/french.mysite.mg`的新文件中：

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

1. 在同一目录中创建另一个名为`german.mysite.mg`的文件，其内容如下：

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

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   如果显示错误，请检查虚拟主机配置文件的语法。

1. 在`/etc/nginx/sites-enabled`目录中创建符号链接：

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
>请勿编辑`nginx.conf.sample`文件；该文件是一个核心Commerce文件，可能会随每个新版本进行更新。 请改为复制`nginx.conf.sample`文件，重命名该文件，然后编辑复制的文件。

**编辑主应用程序的PHP入口点**：

要修改`nginx.conf.sample`文件**：

1. 打开文本编辑器并查看`nginx.conf.sample`文件，`<magento2_installation_directory>/nginx.conf.sample`。 查找以下部分：

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

1. 在include语句前使用以下两行更新`nginx.conf.sample`文件：

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

您必须在Commerce管理员中更新`french`和`german`网站的基本URL。

### 更新法语网站基本URL

1. 登录到Commerce管理员并导航到&#x200B;**商店** > **设置** > **配置** > **常规** > **Web**。
1. 将&#x200B;_配置作用域_&#x200B;更改为`french`网站。
1. 展开&#x200B;**基本URL**&#x200B;部分并将&#x200B;**基本URL**&#x200B;和&#x200B;**基本链接URL**&#x200B;值更新为`http://french.magento24.com/`。
1. 展开&#x200B;**基本URL （安全）**&#x200B;部分并将&#x200B;**安全基本URL**&#x200B;和&#x200B;**安全基本链接URL**&#x200B;值更新为`https://french.magento24.com/`。
1. 单击&#x200B;**保存配置**&#x200B;并保存配置更改。

### 更新德语网站基本URL

1. 登录到Commerce管理员并导航到&#x200B;**商店** > **设置** > **配置** > **常规** > **Web**。
1. 将&#x200B;_配置作用域_&#x200B;更改为`german`网站。
1. 展开&#x200B;**基本URL**&#x200B;部分并将&#x200B;**基本URL**&#x200B;和&#x200B;**基本链接URL**&#x200B;值更新为`http://german.magento24.com/`。
1. 展开&#x200B;**基本URL （安全）**&#x200B;部分并将&#x200B;**安全基本URL**&#x200B;和&#x200B;**安全基本链接URL**&#x200B;值更新为`https://german.magento24.com/`。
1. 单击&#x200B;**保存配置**&#x200B;并保存配置更改。

### 清理缓存

运行以下命令以清理`config`和`full_page`缓存。

```bash
bin/magento cache:clean config full_page
```

## 验证您的站点

除非您为商店的URL设置了DNS，否则必须在`hosts`文件中添加指向主机的静态路由：

1. 找到操作系统`hosts`文件。
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
>- 在托管环境中部署多个网站可能需要执行其他任务；有关更多信息，请咨询您的托管提供商。
>- 在云基础架构上设置Adobe Commerce需要执行其他任务；请参阅[云基础架构上的Commerce指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=zh-Hans)中的&#x200B;_设置多个云网站或商店_。

### 故障排除

- 如果您的法语和德语网站返回404但您的管理员加载了，请确保您已完成[步骤6：将商店代码添加到基本URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url)。
- 如果所有URL都返回404，请确保已重新启动Web服务器。
- 如果管理员无法正常运行，请确保正确设置虚拟主机。
