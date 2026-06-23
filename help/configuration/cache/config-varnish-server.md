---
title: 为清漆缓存配置nginx
description: 了解如何配置Web服务器以使用Adobe Commerce的Varnish缓存。 了解端口配置和设置要求。
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
autotag-review: '2026-06-22T21:49:41.837Z'
TQID: 'https://experienceleague.adobe.com/0vOg86gRkST8CZGhdIESzhld63HQ5IUlO4go-Hgw9Xs'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: c8faa589c9e9d1dbc01863d90aad5f91b11c0140
workflow-type: tm+mt
source-wordcount: 806
ht-degree: 0%

---

# 为Varnish缓存配置nginx {#configure-web-server-for-varnish-caching}

当Varnish用作Adobe Commerce前面的全页缓存时，Varnish通常侦听公共HTTP端口并将请求转发到非默认后端端口（如8080）上的nginx。 更新Commerce源服务器的nginx站点配置，以便在Varnish将使用的后端端口上进行侦听。

{{varnish-config-cloud}}

以下部分使用端口8080作为示例。

**更改Commerce原始服务器的nginx侦听端口**：

1. 在文本编辑器中打开Adobe Commerce源服务器的nginx站点配置。

位置取决于您的操作系统和nginx布局。 例如，Ubuntu通常使用`/etc/nginx/sites-available/`下的文件。

1. 在Commerce站点的`server`块中，将`listen`指令从公共HTTP端口更改为Varnish用于访问nginx的后端端口。

   例如，更改

   ```conf
   server {
       listen 80;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   至：

   ```conf
   server {
       listen 8080;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

1. 保存文件。

1. 验证nginx配置：

   ```shell
   nginx -t
   ```

1. 重新启动nginx：

   ```shell
   systemctl restart nginx
   ```

## 修改Varnish系统配置

更新nginx以侦听后端端口后，将Varnish配置为将请求转发到该主机和端口。 例如：

```conf
backend default {
    .host = "192.0.2.55";
    .port = "8080";
}
```

### 修改缺省VCL

本节讨论如何提供最小配置，以便Varnish返回HTTP响应标头。 这使您可以在配置[!DNL Commerce]应用程序使用Varnish之前验证Varnish是否正常工作。

要最大限度地配置清漆，请执行以下操作：

1. 备份`default.vcl`：

   ```shell
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 在文本编辑器中打开`/etc/varnish/default.vcl`。
1. 找到以下段：

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. 将`.host`的值替换为Varnish _后端_&#x200B;或&#x200B;_原始服务器_&#x200B;的完全限定的主机名或IP地址和侦听端口；即，提供内容Varnish的服务器将加速。

   通常，这是您的Web服务器。 请参阅&#x200B;_清漆指南_&#x200B;中的[后端服务器](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html)。

1. 将`.port`的值替换为Web服务器的侦听端口（在此示例中为8080）。

   示例： nginx安装在主机192.0.2.55上并在端口8080上侦听：

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >如果Varnish和nginx在同一主机上运行，Adobe建议您使用IP地址或主机名，而不是`localhost`。

1. 将更改保存到`default.vcl`并退出文本编辑器。

1. 重新启动清漆：

   ```shell
   service varnish restart
   ```

如果Varnish无法启动，请尝试从命令行运行它，如下所示：

```shell
varnishd -d -f /etc/varnish/default.vcl
```

这应显示错误消息。


>[!INFO]
>
>如果Varnish未作为服务启动，则必须配置SELinux规则以允许其运行。

## 验证清漆是否正常工作

以下各节讨论如何验证Varnish是否正常工作，但&#x200B;_不使用_&#x200B;配置Commerce以使用它。 在配置Commerce之前，您应该尝试此操作。

按照显示的顺序执行以下各节中讨论的任务：

- [开始涂漆](#start-varnish)
- [`netstat`](#netstat)

### 开始涂漆

输入： `service varnish start`

如果Varnish无法作为服务启动，请从命令行启动它，如下所示：

1. 启动Varnish CLI：

   ```shell
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. 启动Varnish子进程：

   出现提示时，输入`start`

   将显示以下消息以确认成功启动：

   ```text
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

登录到Varnish服务器并输入以下命令：

```shell
netstat -tulpn
```

请特别查找以下输出：

```text
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/nginx
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

前文显示了在端口80上运行的Varnish和在端口8080上运行的nginx。

如果未看到`varnishd`的输出，请确保Varnish正在运行。

查看[`netstat`选项](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html)。

## 安装Commerce软件

安装Commerce软件（如果尚未安装）。 当提示输入基本URL时，请使用Varnish主机和端口80（用于Varnish），因为Varnish接收所有传入的HTTP请求。

安装Commerce时可能出错：

```text
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

如果您遇到此错误，请编辑`default.vcl`并向`backend`段添加超时，如下所示：

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## 验证HTTP响应标头

现在，您可以通过查看从任何页面返回的HTML响应标头来验证Varnish是否正在为页面提供服务。

在查看标头之前，必须为开发人员模式设置Commerce 。 有几种方法可以做到这一点，最简单的方法是修改Commerce应用程序根中的`.htaccess`。 您还可以使用[`magento deploy:mode:set`](../cli/set-mode.md)命令。

### 为开发人员模式设置Commerce

要将Commerce设置为开发人员模式，请使用[`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode)命令。

### 看看光泽的日志

确保Varnish正在运行，然后在Varnish服务器上输入以下命令：

```shell
varnishlog
```

在Web浏览器中，转到任何Commerce页面。

命令提示符窗口中会显示一个响应标头的长列表。 查找类似于以下内容的标头：

```text
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

如果此类标头&#x200B;_不_&#x200B;显示，请停止Varnish，检查您的`default.vcl`，然后重试。

### 查看HTML响应标头

查看响应标头的方法有多种，包括使用浏览器插件或浏览器检查器。

以下示例使用`curl`。 您可以从任何可以使用HTTP访问Commerce服务器的计算机输入此命令。

```shell
curl -I -v --location-trusted '<your Commerce base URL>'
```

例如，

```shell
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

查找类似于以下内容的标头：

```text
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
