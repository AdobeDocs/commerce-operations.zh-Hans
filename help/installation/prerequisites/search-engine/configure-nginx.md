---
title: 为搜索引擎配置Ninx
description: 请按照以下步骤使用Nginx Web服务器配置搜索引擎，以在本地安装Adobe Commerce和Magento Open Source。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---


# 为搜索引擎配置Ninx

{{$include /help/_includes/web-server-communication.md}}

## 设置代理

>[!NOTE]
>
>2.4.4中添加了OpenSearch支持。 OpenSearch是一个兼容的分支Elasticsearch。 请参阅 [将Elasticsearch迁移到OpenSearch](../../../upgrade/prepare/opensearch-migration.md) 以了解更多信息。

本节将讨论如何将nginx配置为 *不安全* 代理，以便Adobe Commerce可以使用在此服务器上运行的搜索引擎。 本节不讨论设置HTTP Basic身份验证；中讨论的 [与nginx的安全通信](#secure-communication-with-nginx).

>[!NOTE]
>
>此示例中代理未受保护的原因是，更便于设置和验证。 如果需要，可以将此代理与TLS一起使用；为此，请确保将代理信息添加到安全服务器块配置中。

### 在全局配置中指定其他配置文件

确保您的全局 `/etc/nginx/nginx.conf` 包含以下行，以便加载以下部分中讨论的其他配置文件：

```conf
include /etc/nginx/conf.d/*.conf;
```

### 将nginx设置为代理

本节讨论如何指定谁可以访问Ginx服务器。

1. 使用文本编辑器创建文件 `/etc/nginx/conf.d/magento_es_auth.conf` ，其内容如下：

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. 重新启动初始值：

   ```bash
   service nginx restart
   ```

1. 通过输入以下命令验证代理是否正常工作：

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例如，如果您的代理使用端口8080:

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

## 与nginx的安全通信

本节将讨论如何设置 [HTTP基本身份验证](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) 安全代理。 将TLS和HTTP Basic身份验证结合使用，可阻止任何人拦截与Elasticsearch、OpenSearch或您的应用程序服务器的通信。

由于本机支持HTTP Basic身份验证，因此我们建议通过（例如） [摘要身份验证](https://www.nginx.com/resources/wiki/modules/auth_digest/)，不建议在生产中使用。

其他资源：

* [如何在Ubuntu 14.04（数字海洋）上使用Nginx设置密码身份验证](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [使用Nginx进行基本的HTTP身份验证(HotoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [用于Elasticsearch的Nginx配置示例](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

有关更多信息，请参阅以下部分：

* [创建密码](#create-a-password)
* [设置对Nginx的访问权限](#set-up-access-to-nginx)
* [为搜索引擎设置受限上下文](#set-up-a-restricted-context-for-the-search-engine)
* [验证通信是否安全](#secure-communication-with-nginx)

### 创建密码

我们建议您使用Apache `htpasswd` 命令对具有Elasticsearch或OpenSearch访问权限的用户（已命名）的密码进行编码 `magento_elasticsearch` )。

要创建密码，请执行以下操作：

1. 输入以下命令以确定 `htpasswd` 已安装：

   ```bash
   which htpasswd
   ```

   如果显示路径，则安装该路径；如果命令不返回输出， `htpasswd` 未安装。

1. 如有必要，请安装 `htpasswd`:

   * 乌本图： `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. 创建 `/etc/nginx/passwd` 用于存储密码的目录：

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >出于安全考虑， `<filename>` 应该隐藏；也就是说，它必须从一段时期开始。

1. *（可选）。* 要向密码文件中添加其他用户，请输入相同的命令，而不使用 `-c` （创建）选项：

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. 验证的内容 `/etc/nginx/passwd` 是正确的。

### 设置对Nginx的访问权限

本节讨论如何指定谁可以访问Ginx服务器。

>[!WARNING]
>
>显示的示例适用于 *不安全* 代理。 要使用安全代理，请将以下内容（监听端口除外）添加到安全服务器块。

使用文本编辑器修改 `/etc/nginx/conf.d/magento_es_auth.conf` （不安全）或您的安全服务器块，其中包含以下内容：

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
>上例中显示的搜索引擎监听端口仅为示例。 出于安全考虑，我们建议您使用非默认监听端口。

### 为搜索引擎设置受限上下文

本节讨论如何指定谁可以访问搜索引擎服务器。

1. 输入以下命令以创建用于存储身份验证配置的目录：

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. 使用文本编辑器创建文件 `/etc/nginx/auth/magento_elasticsearch.conf` ，其内容如下：

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

1. 如果设置安全代理，请删除 `/etc/nginx/conf.d/magento_es_auth.conf`.
1. 重新启动Nix并继续下一节：

   ```bash
   service nginx restart
   ```

#### 验证

{{$include /help/_includes/verify-secure-communication.md}}
