---
title: 为Commerce配置清漆
description: 了解如何更新和管理您的Commerce应用程序清漆配置文件。
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# 配置Commerce应用程序以使用Varnish

要将Commerce配置为使用涂漆，请执行以下操作：

1. 以管理员身份登录到管理员。
1. 单击“**[!UICONTROL Stores]**”>“设置”>“**配置**”>“**高级**”>“**系统**”>“**全页缓存**”。
1. 在&#x200B;**[!UICONTROL Caching Application]**&#x200B;列表中，单击&#x200B;**清漆缓存**。
1. 在&#x200B;**[!UICONTROL TTL for public content]**&#x200B;字段中输入值。
1. 展开&#x200B;**[!UICONTROL Varnish Configuration]**&#x200B;并输入以下信息：

   | 字段 | 描述 |
   | ----- | ----------- |
   | 访问列表 | 输入要使其内容失效的完全限定的主机名、IP地址或[无类域间路由(CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking)表示法IP地址范围。 请参阅[清漆缓存清除](https://varnish-cache.org/docs/3.0/tutorial/purging.html)。 |
   | 后端主机 | 输入完全限定的主机名或IP地址，并侦听Varnish _后端_&#x200B;或&#x200B;_原始服务器_&#x200B;的端口；即，提供内容Varnish的服务器将加速。 通常，这是您的Web服务器。 查看[清漆缓存后端服务器](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html)。 |
   | 后端端口 | 源服务器的侦听端口。 |
   | 宽限期 | 确定在后端无响应时，Varnish提供过时内容的时长。 默认值为300秒。 |
   | 处理参数大小 | 指定全页缓存的[`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) HTTP终结点上要处理的[布局句柄](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles)的最大数量。 限制大小可以提高安全性和性能。 默认值为100。 |

1. 单击&#x200B;**保存配置**。

您还可以使用C命令行界面工具从命令行激活Varnish，而不是登录到Admin：

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## 导出Varnish配置文件

要从Admin导出Varnish配置文件：

1. 单击其中一个导出按钮以创建可与“清漆”一起使用的`varnish.vcl`。

   例如，如果您有Varnish 4，请单击&#x200B;**Export VCL for Varnish 4**

   下图显示了一个示例：

   ![将Commerce配置为在管理员中使用Varnish](../../assets/configuration/varnish-admin-22.png)

1. 备份您现有的`default.vcl`。 然后将您刚刚导出的`varnish.vcl`文件重命名为`default.vcl`。 然后将文件复制到`/etc/varnish/`目录。

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe建议您打开`default.vcl`并将`acl purge`的值更改为Varnish主机的IP地址。 （您可以在单独的行上指定多个主机，也可以使用CIDR表示法。）

   例如，

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. 如果要自定义Vagrant运行状况检查或宽限模式或saint模式配置，请参阅[高级清漆配置](config-varnish-advanced.md)。

1. 重新启动Varnish和您的Web服务器：

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 缓存静态文件

默认情况下，不应缓存静态文件，但如果要缓存它们，可以编辑VCL中的部分`Static files caching`以包含以下内容：

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

在配置Commerce以使用Varnish之前，您必须进行这些更改。
