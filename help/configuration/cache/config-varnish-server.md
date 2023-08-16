---
title: 配置Web服务器
description: 了解如何配置Web服务器以使用Varnish。
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# 配置Web服务器

将Web服务器配置为在默认端口80以外的端口上侦听，因为Varnish直接响应传入的HTTP请求，而不是Web服务器。

以下部分使用端口8080作为示例。

**更改Apache 2.4侦听端口**：

1. 打开 `/etc/httpd/conf/httpd.conf` 在文本编辑器中。
1. 找到 `Listen` 指令。
1. 将侦听端口的值更改为 `8080`. （可以使用任何可用的侦听端口。）
1. 将更改保存到 `httpd.conf` 并退出文本编辑器。

## 修改Varnish系统配置

要修改Varnish系统配置：

1. 作为用户，具有 `root` 权限，在文本编辑器中打开Vanish配置文件：

   - CentOS 6： `/etc/sysconfig/varnish`
   - CentOS 7： `/etc/varnish/varnish.params`
   - Debian： `/etc/default/varnish`
   - Ubuntu： `/etc/default/varnish`

1. 将Varnish侦听端口设置为80：

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   对于Varnish 4.x，请确保DAEMON_OPTS包含正确的侦听端口 `-a` 参数（即使VARNISH_LISTEN_PORT设置为正确的值）：

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. 将更改保存到Varnish配置文件并退出文本编辑器。

### 修改缺省VCL

本节讨论如何提供最小配置，以便Varnish返回HTTP响应标头。 这使您可以在配置 [!DNL Commerce] 申请使用Varnish。

要最大限度地配置清漆，请执行以下操作：

1. 备份 `default.vcl`：

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 打开 `/etc/varnish/default.vcl` 在文本编辑器中。
1. 找到以下段：

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. 替换的值 `.host` 完全限定的主机名或IP地址，以及Varnish的侦听端口 _后端_ 或 _原始服务器_；也就是说，提供内容Varnish的服务器将加速。

   通常，这是您的Web服务器。 请参阅 [后端服务器](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) 在 _清漆指南_.

1. 替换的值 `.port` Web服务器的侦听端口（本例中为8080）。

   示例： Apache安装在主机192.0.2.55上，Apache在端口8080上监听：

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >如果Varnish和Apache在同一台主机上运行，Adobe建议您使用IP地址或主机名，而不是 `localhost`.

1. 将更改保存到 `default.vcl` 并退出文本编辑器。

1. 重新启动清漆：

   ```bash
   service varnish restart
   ```

如果Varnish无法启动，请尝试从命令行运行它，如下所示：

```bash
varnishd -d -f /etc/varnish/default.vcl
```

这应显示错误消息。


>[!INFO]
>
>如果Varnish未作为服务启动，则必须配置SELinux规则以允许其运行。

## 验证清漆是否正常工作

以下各节将讨论如何验证清漆是否正常工作， _不含_ 配置Commerce以使用它。 您应在配置Commerce之前尝试此操作。

按照显示的顺序执行以下各节中讨论的任务：

- [开始涂漆](#start-varnish)
- [&#39;netstat&#39;](#netstat)

### 开始涂漆

输入： `service varnish start`

如果Varnish无法作为服务启动，请从命令行启动它，如下所示：

1. 启动Varnish CLI：

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. 启动Varnish子进程：

   出现提示时，输入 `start`

   将显示以下消息以确认成功启动：

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

登录到Varnish服务器并输入以下命令：

```bash
netstat -tulpn
```

请特别查找以下输出：

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

前文显示了在端口80上运行的Varnish和在端口8080上运行的Apache。

如果您看不到以下项的输出： `varnishd`，确保Varnish正在运行。

请参阅 [`netstat` options](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## 安装Commerce软件

安装Commerce软件（如果尚未安装）。 当提示输入基本URL时，请使用Varnish主机和端口80（用于Varnish），因为Varnish接收所有传入的HTTP请求。

安装Commerce时可能出现错误：

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

如果遇到此错误，请编辑 `default.vcl` 并将超时添加到 `backend` 节如下：

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## 验证HTTP响应标头

现在，您可以通过查看从任何页面返回的HTML响应标头来验证Varnish是否正在为页面提供服务。

在查看标头之前，必须为开发人员模式设置Commerce 。 有多种方法可以做到这一点，最简单的方法是进行修改 `.htaccess` 在Commerce应用程序的根中。 您也可以使用 [`magento deploy:mode:set`](../cli/set-mode.md) 命令。

### 为开发人员模式设置Commerce

要将Commerce设置为开发人员模式，请使用 [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) 命令。

### 看看光泽的日志

确保Varnish正在运行，然后在Varnish服务器上输入以下命令：

```bash
varnishlog
```

在Web浏览器中，转到任何Commerce页面。

命令提示符窗口中会显示一个响应标头的长列表。 查找类似于以下内容的标头：

```terminal
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

如果此类标头可以 _非_ 显示，停止Varnish，查看 `default.vcl`，然后重试。

### 查看HTML响应标头

查看响应标头的方法有多种，包括使用浏览器插件或浏览器检查器。

以下示例使用 `curl`. 您可以从任何可以使用HTTP访问Commerce服务器的计算机输入此命令。

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

例如，

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

查找类似于以下内容的标头：

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
