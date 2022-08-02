---
title: 为商务或Magento配置清漆
description: 了解如何更新和管理商务应用程序的清漆配置文件。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# 配置商务应用程序以使用清漆

要将商务配置为使用清漆，请执行以下操作：

1. 以管理员身份登录。
1. 单击 **[!UICONTROL Stores]** >设置> **配置** > **高级** > **系统** > **全页缓存**.
1. 从 **[!UICONTROL Caching Application]** 列表，单击 **清漆缓存**.
1. 在 **[!UICONTROL TTL for public content]** 字段。
1. 展开 **[!UICONTROL Varnish Configuration]** 并输入以下信息：

   | 字段 | 描述 |
   | ----- | ----------- |
   | 访问列表 | 输入完全限定的主机名、IP地址或 [无类域间路由(CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) 表示无效内容的IP地址范围。 请参阅 [清漆缓存清除](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | 后端主机 | 输入清漆的完全限定的主机名或IP地址和侦听端口 _后端_ 或 _源服务器_;也就是说，提供清漆内容的服务器会加速。 通常，这是您的Web服务器。 请参阅 [清漆缓存后端服务器](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | 后端端口 | 源服务器的侦听端口。 |
   | 宽限期 | 如果后端无响应，则宽限期可确定清漆提供过时内容的时长。 默认值为300秒。 |

1. 单击 **保存配置**.

您还可以使用C命令行界面工具从命令行中激活清漆（而不是登录到管理员）：

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## 导出清漆配置文件

要从管理员导出清漆配置文件，请执行以下操作：

1. 单击其中一个导出按钮可创建 `varnish.vcl` 你可以用清漆。

   例如，如果有清漆4，请单击 **用于清漆4的导出VCL**

   下图显示了一个示例：

   ![在管理员中配置商务以使用清漆](../../assets/configuration/varnish-admin-22.png)

1. 备份现有 `default.vcl`. 然后，重命名 `varnish.vcl` 您刚刚导出到的文件 `default.vcl`. 然后，将文件复制到 `/etc/varnish/` 目录访问Advertising Cloud的帮助。

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe建议您打开 `default.vcl` 并更改 `acl purge` 到清漆主机的IP地址。 （您可以在单独的行上指定多个主机，也可以使用CIDR表示法。）

   例如，

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. 如果要自定义流浪健康检查或宽限模式或saint模式配置，请参阅 [高级清漆配置](config-varnish-advanced.md).

1. 重新启动清漆和Web服务器：

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 缓存静态文件

默认情况下不应缓存静态文件，但如果要缓存静态文件，可以编辑部分 `Static files caching` （在VCL中）具有以下内容：

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

在将“商务”配置为使用清漆之前，您必须进行这些更改。
