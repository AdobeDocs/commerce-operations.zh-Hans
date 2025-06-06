---
title: 为搜索引擎配置Nginx
description: 按照以下步骤使用Nginx Web服务器配置搜索引擎，用于Adobe Commerce的内部安装。
feature: Install, Search
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# 为搜索引擎配置Nginx

{{$include /help/_includes/web-server-communication.md}}

## 设置代理

>[!NOTE]
>
>2.4.4中添加了OpenSearch支持。OpenSearch是兼容的Elasticsearch分支。 有关详细信息，请参阅[将Elasticsearch迁移到OpenSearch](../../../upgrade/prepare/opensearch-migration.md)。

本节讨论如何将nginx配置为&#x200B;*不安全*&#x200B;代理，以便Adobe Commerce能够使用在此服务器上运行的搜索引擎。 本节不讨论设置HTTP基本身份验证；这将在与nginx[&#128279;](#secure-communication-with-nginx)的安全通信中讨论。

>[!NOTE]
>
>在此示例中，代理不受保护的原因是它更容易设置和验证。 如果需要，可以将TLS与此代理一起使用；要这样做，请确保将代理信息添加到安全服务器块配置中。

### 在全局配置中指定其他配置文件

请确保您的全局`/etc/nginx/nginx.conf`包含以下行，以便加载以下部分中讨论的其他配置文件：

```conf
include /etc/nginx/conf.d/*.conf;
```

### 将nginx设置为代理

本节讨论如何指定谁可以访问nginx服务器。

1. 使用文本编辑器创建包含以下内容的文件`/etc/nginx/conf.d/magento_es_auth.conf`：

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. 重新启动nginx：

   ```bash
   service nginx restart
   ```

1. 通过输入以下命令验证代理是否正常工作：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，如果您的代理使用端口8080：

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   类似于以下内容的消息显示成功：

   ```
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## 与nginx的安全通信

本节讨论如何使用安全代理设置[HTTP基本身份验证](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html)。 同时使用TLS和HTTP Basic身份验证可防止任何人截获与Elasticsearch、OpenSearch或您的应用程序服务器的通信。

由于nginx本身支持HTTP基本身份验证，因此我们建议将其覆盖，例如[摘要式身份验证](https://www.nginx.com/resources/wiki/modules/auth_digest/)，在生产环境中不建议这样做。

其他资源：

* [如何在Ubuntu 14.04 (Digital Ocean)上设置Nginx的密码身份验证](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [使用Nginx (HowtoForge)进行基本HTTP身份验证](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Elasticsearch的Nginx配置示例](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

有关更多信息，请参阅以下部分：

* [创建密码](#create-a-password)
* [设置对nginx的访问权限](#set-up-access-to-nginx)
* [为搜索引擎设置受限制的上下文](#set-up-a-restricted-context-for-the-search-engine)
* [验证通信是否安全](#secure-communication-with-nginx)

### 创建密码

我们建议您使用Apache `htpasswd`命令为有权访问Elasticsearch或OpenSearch（在此示例中名为`magento_elasticsearch`）的用户编码密码。

要创建密码，请执行以下操作：

1. 输入以下命令以确定是否已安装`htpasswd`：

   ```bash
   which htpasswd
   ```

   如果显示路径，则表明已安装；如果命令未返回任何输出，则表明未安装`htpasswd`。

1. 如有必要，请安装`htpasswd`：

   * Ubuntu： `apt-get -y install apache2-utils`
   * CentOS： `yum -y install httpd-tools`

1. 创建`/etc/nginx/passwd`目录以存储密码：

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >出于安全原因，`<filename>`应隐藏；即，它必须以句点开头。

1. *（可选）。*&#x200B;若要向密码文件添加其他用户，请输入相同的命令，但不使用`-c` （创建）选项：

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. 验证`/etc/nginx/passwd`的内容是否正确。

### 设置对nginx的访问权限

本节讨论如何指定谁可以访问nginx服务器。

>[!WARNING]
>
>显示的示例适用于&#x200B;*不安全*&#x200B;代理。 要使用安全代理，请将以下内容（监听端口除外）添加到安全服务器块。

使用文本编辑器修改`/etc/nginx/conf.d/magento_es_auth.conf`（不安全）或您的安全服务器块，内容如下：

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>上例中显示的搜索引擎侦听端口仅为示例。 出于安全原因，我们建议您使用非默认监听端口。

### 为搜索引擎设置受限制的上下文

本节将讨论如何指定可以访问搜索引擎服务器的用户。

1. 输入以下命令创建用于存储身份验证配置的目录：

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. 使用文本编辑器创建包含以下内容的文件`/etc/nginx/auth/magento_elasticsearch.conf`：

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. 如果您设置了安全代理，请删除`/etc/nginx/conf.d/magento_es_auth.conf`。
1. 重新启动nginx并继续下一部分：

   ```bash
   service nginx restart
   ```

#### 验证

{{$include /help/_includes/verify-secure-communication.md}}
