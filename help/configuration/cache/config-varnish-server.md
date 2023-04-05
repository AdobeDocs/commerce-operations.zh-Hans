---
title: 配置Web服务器
description: 了解如何配置Web服务器以使用清漆。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---


# 配置Web服务器

将Web服务器配置为监听默认端口80以外的端口，因为Quest直接响应传入的HTTP请求，而不是Web服务器。

以下部分以端口8080为例。

**更改Apache 2.4侦听端口**:

1. 打开 `/etc/httpd/conf/httpd.conf` 在文本编辑器中。
1. 找到 `Listen` 指令。
1. 将侦听端口的值更改为 `8080`. （您可以使用任何可用的监听端口。）
1. 将更改保存到 `httpd.conf` 并退出文本编辑器。

## 修改清漆系统配置

要修改清漆系统配置，请执行以下操作：

1. 作为用户， `root` 权限，请在文本编辑器中打开您的“消失”配置文件：

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - 乌本图： `/etc/default/varnish`

1. 将清漆侦听端口设置为80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   对于Imest 4.x，请确保DAEMON_OPTS包含正确的侦听端口 `-a` 参数（即使将RIKEST_LISTEN_PORT设置为正确的值）：

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. 保存对清漆配置文件所做的更改并退出文本编辑器。

### 修改默认VCL

本节讨论如何提供最小的配置，以便Quiset返回HTTP响应标头。 这样，您就可以在配置 [!DNL Commerce] 使用清漆的应用程序。

要最小化配置清漆，请执行以下操作：

1. 备份 `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 打开 `/etc/varnish/default.vcl` 在文本编辑器中。
1. 找到以下标准：

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. 替换 `.host` 具有完全限定的主机名或IP地址和清漆的侦听端口 _后端_ 或 _源服务器_;即，提供内容清漆的服务器将加速。

   通常，这是您的Web服务器。 请参阅 [后端服务器](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) 在 _清漆引导器_.

1. 替换 `.port` 使用web服务器的监听端口（本示例中为8080）。

   示例：Apache安装在主机192.0.2.55上，Apache在端口8080上侦听：

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >如果清漆和Apache在同一主机上运行，则Adobe建议您使用IP地址或主机名，而不是 `localhost`.

1. 将更改保存到 `default.vcl` 并退出文本编辑器。

1. 重新启动清漆：

   ```bash
   service varnish restart
   ```

如果清漆无法启动，请尝试从命令行中运行它，如下所示：

```bash
varnishd -d -f /etc/varnish/default.vcl
```

这应会显示错误消息。


>[!INFO]
>
>如果清漆不作为服务启动，则必须配置SELinux规则以允许它运行。

## 验证清漆是否正常工作

以下各节讨论如何验证清漆是否正常工作，但 _无_ 配置商务以使用它。 您应该在配置Commerce之前先尝试此操作。

按照显示的顺序执行以下各节中讨论的任务：

- [启动清漆](#start-varnish)
- [“netstat”](#netstat)

### 启动清漆

输入： `service varnish start`

如果清漆作为服务启动失败，请从命令行启动它，如下所示：

1. 启动清漆CLI:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. 启动清漆子进程：

   出现提示时，输入 `start`

   将显示以下消息以确认启动成功：

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

登录到清漆服务器并输入以下命令：

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

前面显示在端口80上运行清漆，在端口8080上运行Apache。

如果看不到的输出 `varnishd`，确保清漆正在运行。

请参阅 [`netstat` 选项](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## 安装商务软件

安装商务软件（如果尚未安装）。 提示输入基本URL时，请使用清漆主机和端口80（对于清漆），因为清漆接收所有传入的HTTP请求。

安装商务时可能出错：

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

如果您遇到此错误，请编辑 `default.vcl` 并向 `backend` 斯坦扎如下：

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## 验证HTTP响应头

现在，您可以通过查看从任何页面返回的HTML响应标头来验证清漆是否正在提供页面。

在查看标题之前，必须先为开发人员模式设置商务。 可以通过多种方法来执行此操作，其中最简单的方法就是修改 `.htaccess` （在商务应用程序根目录中）。 您还可以使用 [`magento deploy:mode:set`](../cli/set-mode.md) 命令。

### 为开发人员模式设置商务

要为开发人员模式设置商务，请使用 [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) 命令。

### 看清漆日志

确保清漆正在运行，然后在清漆服务器上输入以下命令：

```bash
varnishlog
```

在Web浏览器中，转到任何商务页面。

在命令提示符窗口中将显示响应标头的长列表。 查找如下所示的标头：

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

如果此类标头有 _not_ 显示，停止清漆，检查 `default.vcl`，然后重试。

### 查看HTML响应标头

有多种方法可查看响应标头，包括使用浏览器插件或浏览器检查器。

以下示例使用 `curl`. 您可以从任何能够使用HTTP访问商务服务器的计算机中输入此命令。

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

例如，

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

查找如下所示的标头：

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
