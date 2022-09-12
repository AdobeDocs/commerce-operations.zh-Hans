---
title: 为搜索引擎配置Apache
description: 请按照以下步骤使用Apache Web服务器配置搜索引擎，以在本地安装Adobe Commerce和Magento Open Source。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 为搜索引擎配置Apache

{{$include /help/_includes/web-server-communication.md}}

## 设置代理

>[!NOTE]
>
>2.4.4中添加了OpenSearch支持。 OpenSearch是一个兼容的分支Elasticsearch。 配置Elasticsearch7的所有说明都适用于OpenSearch。 请参阅 [将Elasticsearch迁移到OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 以了解更多信息。

本节将讨论如何将Apache配置为 *不安全* 代理，以便Adobe Commerce或Magento Open Source可以使用在此服务器上运行的搜索引擎。 本节不讨论设置HTTP Basic身份验证；中讨论的 [与Apache的安全通信](#secure-communication-with-apache).

>[!NOTE]
>
>此示例中代理未受保护的原因是，更便于设置和验证。 您可以将此代理与TLS结合使用。 如果您希望这样做，请确保将代理信息添加到安全虚拟主机配置中。

### 设置Apache 2.4的代理

本节讨论如何使用虚拟主机配置代理。

1. 启用 `mod_proxy` 如下所示：

   ```bash
   a2enmod proxy_http
   ```

1. 使用文本编辑器打开 `/etc/apache2/sites-available/000-default.conf`
1. 在文件顶部添加以下指令：

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

1. 重新启动Apache:

   ```bash
   service apache2 restart
   ```

1. 通过输入以下命令验证代理是否正常工作：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，如果您使用Elasticsearch，而代理使用端口8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   与以下显示类似的消息，用于指示成功：

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## 与Apache的安全通信

本节讨论如何使用 [HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617) 身份验证。 有关更多选项，请咨询以下资源之一：

* [Apache 2.4身份验证和授权教程](https://httpd.apache.org/docs/2.4/howto/auth.html)

请参阅以下部分之一：

* [创建密码文件](#create-a-password)
* [配置安全虚拟主机](#secure-communication-with-apache)

### 创建密码

出于安全考虑，您可以在除Web服务器Docroot之外的任意位置找到密码文件。 在本例中，我们将演示如何将密码文件存储到新目录中。

#### 如有必要，请安装htpasswd

首先，看看你是否拥有Apache `htpasswd` 实用程序安装如下：

1. 输入以下命令以确定 `htpasswd` 已安装：

   ```bash
   which htpasswd
   ```

   如果显示路径，则安装该路径；如果命令不返回输出， `htpasswd` 未安装。

1. 如有必要，请安装 `htpasswd`:

   * 乌本图： `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### 创建密码文件

以用户身份输入以下命令 `root` 权限：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

其中

* `<username>` 可以是：

   * 设置开头：Web服务器用户或其他用户。

   在本例中，我们使用Web服务器用户，但用户的选择取决于您。

   * 设置Elasticsearch:用户名为 `magento_elasticsearch` 在本例中


* `<password file name>` 必须是隐藏文件(开头为 `.`)，且应反映用户的名称。 有关详细信息，请参阅此部分后面的示例。

按照屏幕上的提示为用户创建密码。

#### 示例

**示例1:cron**
您必须仅为一个用户设置CRON身份验证；在本例中，我们使用web服务器用户。 要为Web服务器用户创建密码文件，请输入以下命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**示例2:Elasticsearch**
您必须为两个用户设置身份验证：一个具有nginx访问权限，另一个具有Elasticsearch权限。 要为这些用户创建密码文件，请输入以下命令：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### 添加其他用户

要向密码文件中添加其他用户，请输入以下命令作为用户，其中 `root` 权限：

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### 与Apache的安全通信

本节将讨论如何设置 [HTTP基本身份验证](https://httpd.apache.org/docs/2.2/howto/auth.html). 将TLS和HTTP Basic身份验证结合使用，可阻止任何人拦截与Elasticsearch或您的应用程序服务器的通信。

本节讨论如何指定谁可以访问Apache服务器。

1. 使用文本编辑器将以下内容添加到安全虚拟主机。

   * Apache 2.4:编辑 `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elastic Server"
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. 如果将前面的添加到安全虚拟主机，请删除 `Listen 8080` 和 `<VirtualHost *:8080>` 您之前添加到不安全虚拟主机的指令。

1. 保存更改，退出文本编辑器，然后重新启动Apache:

   * CentOS: `service httpd restart`
   * 乌本图： `service apache2 restart`

#### 验证

{{$include /help/_includes/verify-secure-communication.md}}
