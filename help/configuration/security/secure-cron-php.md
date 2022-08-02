---
title: 安全CRON PHP
description: 限制谁可以在浏览器中运行cron.php文件。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 1%

---


# 安全CRON PHP

本主题讨论安全 `pub/cron.php` 以防止其被恶意攻击使用。 如果您不保护cron，则任何用户都可能运行cron以攻击您的Commerce应用程序。

cron作业运行多个计划任务，是商务配置的重要部分。 计划任务包括但不限于：

- 重新索引
- 生成电子邮件
- 生成新闻稿
- 生成站点地图

>[!INFO]
>
>请参阅 [配置并运行cron](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) 以了解有关cron组的更多信息。

您可以通过以下方式运行cron作业：

- 使用 [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) 命令行或crontab中的命令
- 访问 `pub/cron.php?[group=<name>]` 在web浏览器中

>[!INFO]
>
>如果使用 [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) 命令来运行cron，因为它使用的进程已经安全。

## 使用Apache保护CRON

本节讨论如何使用Apache的HTTP Basic身份验证来保护CRON。 这些说明基于带有CentOS 6的Apache 2.2。 有关更多信息，请参阅以下资源之一：

- [Apache 2.2身份验证和授权教程](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Apache 2.4身份验证和授权教程](https://httpd.apache.org/docs/2.4/howto/auth.html)

### 创建密码文件

出于安全考虑，您可以在除Web服务器Docroot之外的任意位置找到密码文件。 在本例中，我们将密码文件存储在新目录中。

以用户身份输入以下命令 `root` 权限：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

其中 `<username>` 可以是web服务器用户或其他用户。 在本例中，我们使用Web服务器用户，但用户的选择取决于您。

按照屏幕上的提示为用户创建密码。

要向密码文件中添加其他用户，请输入以下命令作为用户，其中 `root` 权限：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### 添加用户以创建已授权的客户群组（可选）

您可以通过将多个用户添加到密码文件（包括组文件）来启用运行cron的功能。

要向密码文件中添加其他用户，请执行以下操作：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

要创建授权组，请在Web服务器Docroot外的任意位置创建组文件。 组文件指定组的名称和组中的用户。 在本例中，组名称为 `MagentoCronGroup`.

```bash
vim /usr/local/apache/password/group
```

文件内容：

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### 在中安全创建 `.htaccess`

保护CRON `.htaccess` 文件：

1. 以文件系统所有者的身份登录或切换到您的商务服务器。
1. 打开 `<magento_root>/pub/.htaccess` 在文本编辑器中。

   (因为 `cron.php` 位于 `pub` 目录，编辑此 `.htaccess` 只有。)

1. _为一个或多个用户创建访问权限。_ 替换现有 `<Files cron.php>` 指令，其中包括：

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _创建群组的访问权限。_ 替换现有 `<Files cron.php>` 指令，其中包括：

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. 将更改保存到 `.htaccess` 并退出文本编辑器。
1. 继续 [验证cron是否安全](#verify-cron-is-secure).

## 使用Nginx保护CRON

本节讨论如何使用Nginx Web服务器保护CRON。 您必须执行以下任务：

1. 为Nginx设置加密密码文件
1. 修改原始配置，以在访问 `pub/cron.php`

### 创建密码文件

在继续操作之前，请咨询以下资源之一以创建密码文件：

- [如何在Ubuntu 14.04(DigitalOcean)上使用Nginx设置密码身份验证](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [使用Nginx进行基本HTTP身份验证（如何伪造）](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### 在中安全创建 `nginx.conf.sample`

Commerce提供了一个现成的优化示例原始配置文件。 我们建议对其进行修改以保护CRON安全。

1. 在 [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 文件：

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

1.重新启动初始值：

```bash
systemctl restart nginx
```

1. 继续 [验证cron是否安全](#verify-cron-is-secure).

## 验证cron是否安全

最简单的方法来验证 `pub/cron.php` 是安全的，是验证它在 `cron_schedule` 数据库表。 此示例使用SQL命令检查数据库，但您可以使用任何所需工具。

>[!INFO]
>
>的 `default` 您在此示例中运行的cron将根据 `crontab.xml`. 某些cron作业每天只运行一次。 首次从浏览器中运行cron时， `cron_schedule` 表格已更新，但后续 `pub/cron.php` 请求在配置的计划下运行。

**验证cron是否安全**:

1. 以Commerce数据库用户或以 `root`.

   例如，

   ```bash
   mysql -u magento -p
   ```

1. 使用商务数据库：

   ```shell
   use <database-name>;
   ```

   例如，

   ```shell
   use magento;
   ```

1. 删除 `cron_schedule` 数据库表：

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. 从浏览器运行cron:

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   例如：

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. 出现提示时，输入授权用户的名称和密码。 下图显示了一个示例。

   ![使用HTTP Basic授权创建](../../assets/configuration/cron-auth.png)

1. 验证是否已将行添加到表中：

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

您可以随时使用Web浏览器运行Cron，例如在开发期间。

>[!WARNING]
>
>做 _not_ 在浏览器中运行cron，而不先保护它。

如果您使用的是Apache Web服务器，则必须从 `.htaccess` 文件，然后才能在浏览器中运行cron:

1. 以有权写入商务文件系统的用户身份登录到商务服务器。
1. 在文本编辑器中打开以下任意内容(具体取决于您的Magento入口点):

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

- `<your hostname or IP>` 是您的Commerce安装的主机名或IP地址
- `<Commerce root>` 是Web服务器docroot-relative目录，您将Commerce软件安装到该目录中

   运行Commerce应用程序的确切URL取决于您配置Web服务器和虚拟主机的方式。

- `<group name>` 是任何有效的cron组名称（可选）

例如，

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>您必须运行两次cron:首先，发现要运行的任务，然后再次发现要自己运行任务。 请参阅 [配置并运行cron](../cli/configure-cron-jobs.md) 以了解有关cron组的更多信息。
