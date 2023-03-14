---
title: 为搜索引擎配置Apache
description: 按照以下步骤使用Apache Web Server配置搜索引擎，以进行Adobe Commerce和Magento Open Source的内部安装。
source-git-commit: d3cfd97450164d38fd340b538099739601573d64
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# 为搜索引擎配置Apache

{{$include /help/_includes/web-server-communication.md}}

## 设置代理

>[!NOTE]
>
>2.4.4中添加了OpenSearch支持。OpenSearch是兼容的Elasticsearch分支。 参见 [将Elasticsearch迁移到OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 了解更多信息。

本节讨论如何将Apache配置为 *不安全* 代理服务器，以便Adobe Commerce能够使用在此服务器上运行的搜索引擎。 本节不讨论设置HTTP基本身份验证；将在中讨论 [与Apache的安全通信](#secure-communication-with-apache).

>[!NOTE]
>
>在此示例中，代理不安全的原因是它更易于设置和验证。 您可以将TLS与此代理一起使用。 如果要这样做，请确保将代理信息添加到安全虚拟主机配置中。

### 为Apache 2.4设置代理

本节讨论如何使用虚拟主机配置代理。

1. 启用 `mod_proxy` 如下所示：

   ```bash
   a2enmod proxy_http
   ```

1. 使用文本编辑器打开 `/etc/apache2/sites-available/000-default.conf`
1. 在文件的顶部添加以下指令：

   ```conf
   Listen 8080
   ```

1. 在文件底部添加以下内容：

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. 重新启动Apache：

   ```bash
   service apache2 restart
   ```

1. 通过输入以下命令验证代理是否正常工作：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，如果您使用Elasticsearch，而您的代理使用的是端口8080：

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   类似于以下内容的消息显示指示成功：

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## 与Apache的安全通信

本节讨论如何使用保护Apache与搜索引擎之间的通信 [HTTP基本](https://datatracker.ietf.org/doc/html/rfc2617) 使用Apache进行身份验证。 有关更多选项，请参阅以下资源之一：

* [Apache 2.4身份验证和授权教程](https://httpd.apache.org/docs/2.4/howto/auth.html)

请参阅以下部分之一：

* [创建密码文件](#create-a-password)
* [配置安全虚拟主机](#secure-communication-with-apache)

### 创建密码

出于安全原因，您可以在Web服务器docroot以外的任何位置找到口令文件。 在本例中，我们将说明如何将密码文件存储在新目录中。

#### 安装htpasswd（如有必要）

首先，查看您是否拥有Apache `htpasswd` 实用程序安装如下：

1. 输入以下命令以确定是否 `htpasswd` 已安装：

   ```bash
   which htpasswd
   ```

   如果显示路径，则表明已安装；如果命令未返回任何输出， `htpasswd` 未安装。

1. 如有必要，请安装 `htpasswd`：

   * Ubuntu： `apt-get -y install apache2-utils`
   * CentOS： `yum -y install httpd-tools`

#### 创建密码文件

以用户身份输入以下命令 `root` 权限：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

位置

* `<username>` 可以是：

   * 设置cron：Web服务器用户或其他用户。

   在本例中，我们使用Web服务器用户，但用户的选择取决于您。

   * 设置Elasticsearch：用户已命名 `magento_elasticsearch` 在此示例中


* `<password file name>` 必须为隐藏文件(开头为 `.`)，并且应该反映用户的名称。 有关详细信息，请参阅此部分后面的示例。

按照屏幕上的提示为用户创建密码。

#### 示例

**示例1：cron**
您必须为cron仅设置一个用户的身份验证；在本例中，我们使用Web服务器用户。 要为Web服务器用户创建密码文件，请输入以下命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**示例2：Elasticsearch**
您必须为两个用户设置身份验证：一个具有对nginx的访问权限，另一个具有对Elasticsearch的访问权限。 要为这些用户创建密码文件，请输入以下命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### 添加其他用户

要将另一个用户添加到您的密码文件，请以用户身份输入以下命令 `root` 权限：

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### 与Apache的安全通信

本节讨论如何设置 [HTTP基本身份验证](https://httpd.apache.org/docs/2.2/howto/auth.html). 将TLS和HTTP Basic身份验证结合使用可防止任何人拦截与Elasticsearch、OpenSearch或您的应用服务器的通信。

本节讨论如何指定谁可以访问Apache Server。

1. 使用文本编辑器将以下内容添加到您的安全虚拟主机。

   * Apache 2.4：编辑 `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. 如果您已将上述内容添加到安全虚拟主机，请删除 `Listen 8080` 和 `<VirtualHost *:8080>` 您之前添加到不安全的虚拟主机的指令。

1. 保存更改，退出文本编辑器，然后重新启动Apache：

   * CentOS： `service httpd restart`
   * Ubuntu： `service apache2 restart`

#### 验证

{{$include /help/_includes/verify-secure-communication.md}}
