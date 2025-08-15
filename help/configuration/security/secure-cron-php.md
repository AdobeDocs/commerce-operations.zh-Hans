---
title: 安全cron PHP
description: 限制可在浏览器中运行cron.php文件的用户。
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 1%

---

# 安全cron PHP

本主题讨论如何保护`pub/cron.php`以防止其被恶意利用。 如果不保护cron的安全，则任何用户都可能运行cron来攻击您的Commerce应用程序。

cron作业运行多个计划任务，是Commerce配置的重要组成部分。 计划任务包括但不限于：

- 重新索引
- 生成电子邮件
- 生成新闻稿
- 生成站点地图

>[!INFO]
>
>有关cron组的详细信息，请参阅[配置和运行cron](../cli/configure-cron-jobs.md#run-cron-from-the-command-line)。

您可以通过以下方式运行cron作业：

- 从命令行或在crontab中使用[`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line)命令
- 在Web浏览器中访问`pub/cron.php?[group=<name>]`

>[!INFO]
>
>如果您使用[`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line)命令运行cron，则无需执行任何操作，因为它使用其他已安全的进程。

## 使用Apache的Secure cron

本节讨论如何通过Apache使用HTTP基本身份验证来保护cron。 这些说明基于带有CentOS 6的Apache 2.2。 有关更多信息，请参阅以下资源之一：

- [Apache 2.2身份验证和授权教程](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Apache 2.4身份验证和授权教程](https://httpd.apache.org/docs/2.4/howto/auth.html)

### 创建密码文件

出于安全原因，您可以在Web服务器docroot以外的任何位置查找密码文件。 在本例中，我们将密码文件存储在新目录中。

以具有`root`权限的用户身份输入以下命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

其中`<username>`可以是Web服务器用户或另一个用户。 在本例中，我们使用Web服务器用户，但用户的选择取决于您。

按照屏幕上的提示为用户创建密码。

要将其他用户添加到密码文件，请以具有`root`权限的用户身份输入以下命令：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### 添加用户以创建授权的cron组（可选）

通过将多个用户添加到密码文件（包括组文件），您可以启用这些用户运行cron。

要将其他用户添加到密码文件，请执行以下操作：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

要创建授权组，请在Web服务器docroot之外的任意位置创建组文件。 组文件指定组的名称和组中的用户。 在此示例中，组名称为`MagentoCronGroup`。

```bash
vim /usr/local/apache/password/group
```

文件的内容：

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### `.htaccess`中的安全CRON

要在`.htaccess`文件中保护cron：

1. 以文件系统所有者的身份登录Commerce服务器或切换到文件系统所有者。
1. 在文本编辑器中打开`<magento_root>/pub/.htaccess`。

   （由于`cron.php`位于`pub`目录中，请仅编辑此`.htaccess`。）

1. 一个或多个用户的&#x200B;_Cron访问权限。_&#x200B;将现有`<Files cron.php>`指令替换为以下内容：

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. 对组的&#x200B;_Cron访问权限。_&#x200B;将现有`<Files cron.php>`指令替换为以下内容：

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. 将更改保存到`.htaccess`并退出文本编辑器。
1. 继续[验证cron是否安全](#verify-cron-is-secure)。

## 使用Nginx确保Cron安全

本节讨论如何使用Nginx Web服务器保护cron。 您必须执行以下任务：

1. 为Nginx设置加密密码文件
1. 修改您的nginx配置以在访问`pub/cron.php`时引用密码文件

### 创建密码文件

在继续之前，请查阅以下资源之一以创建密码文件：

- [如何在Ubuntu 14.04 (DigitalOcean)上使用Nginx设置密码身份验证](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [具有Nginx的基本HTTP身份验证(howtoforge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### `nginx.conf.sample`中的安全CRON

Commerce提供了一个现成的优化示例nginx配置文件。 我们建议修改它以保护cron。

1. 将以下内容添加到您的[`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)文件：

   ```conf
   #Securing cron
   location ~ cron\.php$ {
      auth_basic "Cron Authentication";
      auth_basic_user_file /etc/nginx/.htpasswd;
   
      try_files $uri =404;
      fastcgi_pass   fastcgi_backend;
      fastcgi_buffers 1024 4k;
   
      fastcgi_read_timeout 600s;
      fastcgi_connect_timeout 600s;
   
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include        fastcgi_params;
   }
   ```

1.重新启动nginx：

```bash
systemctl restart nginx
```

1. 继续[验证cron是否安全](#verify-cron-is-secure)。

## 验证cron是否安全

验证`pub/cron.php`是否安全的最简单方法是，在设置密码身份验证之后，验证它是否在`cron_schedule`数据库表中创建行。 此示例使用SQL命令来检查数据库，但您可以使用任何您喜欢的工具。

>[!INFO]
>
>在此示例中运行的`default` cron将根据`crontab.xml`中定义的计划运行。 某些cron作业每天只运行一次。 第一次从浏览器运行cron时，`cron_schedule`表会更新，但后续`pub/cron.php`请求会按配置的时间表运行。

**验证cron是否安全**：

1. 以Commerce数据库用户或`root`身份登录到数据库。

   例如，

   ```bash
   mysql -u magento -p
   ```

1. 使用Commerce数据库：

   ```shell
   use <database-name>;
   ```

   例如，

   ```shell
   use magento;
   ```

1. 删除`cron_schedule`数据库表中的所有行：

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. 从浏览器运行cron：

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   例如：

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. 出现提示时，输入授权用户的名称和密码。 下图显示了一个示例。

   ![使用HTTP Basic授权cron](../../assets/configuration/cron-auth.png)

1. 验证是否已向表中添加行：

   ```shell
   SELECT * from cron_schedule;
   
   mysql> SELECT * from cron_schedule;
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   | schedule_id | job_code                             | status  | messages | created_at        | scheduled_at      | executed_at | finished_at |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   |         1 | catalog_product_outdated_price_values_cleanup | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         2 | sales_grid_order_async_insert             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         3 | sales_grid_order_invoice_async_insert       | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         4 | sales_grid_order_shipment_async_insert      | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         5 | sales_grid_order_creditmemo_async_insert     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         6 | sales_send_order_emails                  | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         7 | sales_send_order_invoice_emails            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         8 | sales_send_order_shipment_emails           | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         9 | sales_send_order_creditmemo_emails         | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        10 | newsletter_send_all                     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:25:00 | NULL      | NULL      |
   |        11 | captcha_delete_old_attempts               | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        12 | captcha_delete_expired_images             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        13 | outdated_authentication_failures_cleanup     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        14 | magento_newrelicreporting_cron            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   14 rows in set (0.00 sec)
   ```

## 从Web浏览器运行cron

您可以随时使用Web浏览器运行cron，例如在开发期间。

>[!WARNING]
>
>请&#x200B;_不要_&#x200B;在浏览器中运行cron而不先保护它。

如果您使用的是Apache Web Server，则必须先从`.htaccess`文件中删除限制，然后才能在浏览器中运行cron：

1. 以有权写入Commerce文件系统的用户身份登录到Commerce服务器。
1. 在文本编辑器中打开以下任意内容(具体取决于您指向Magento的入口点)：

   ```text
   <magento_root>/pub/.htaccess
   <magento_root>/.htaccess
   ```

1. 删除或注释以下内容：

   ```conf
   ## Deny access to cron.php
     <Files cron.php>
        order allow,deny
        deny from all
     </Files>
   ```

   例如，

   ```conf
   ## Deny access to cron.php
      #<Files cron.php>
         # order allow,deny
         # deny from all
      #</Files>
   ```

1. 保存更改并退出文本编辑器。

   然后，您可以在Web浏览器中运行cron，如下所示：

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

其中：

- `<your hostname or IP>`是Commerce安装的主机名或IP地址
- `<Commerce root>`是安装Commerce软件的Web服务器docroot相对目录

  用于运行Commerce应用程序的确切URL取决于您配置Web服务器和虚拟主机的方式。

- `<group name>`是任何有效的cron组名称（可选）

例如，

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>您必须运行两次cron：首先发现要运行的任务，然后再次运行任务本身。 有关cron组的详细信息，请参阅[配置和运行cron](../cli/configure-cron-jobs.md)。
