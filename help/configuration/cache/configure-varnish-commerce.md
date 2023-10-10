---
title: 配置Commerce清漆
description: 了解如何更新和管理Commerce应用程序的Varnish配置文件。
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 11ccc59230a7a0d1768c043c39df43c7df031efd
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# 配置Commerce应用程序以使用Varnish

要将Commerce配置为使用清漆，请执行以下操作：

1. 以管理员身份登录到管理员。
1. 单击 **[!UICONTROL Stores]** >设置> **配置** > **高级** > **系统** > **全页缓存**.
1. 从 **[!UICONTROL Caching Application]** 列表，单击 **清漆缓存**.
1. 在 **[!UICONTROL TTL for public content]** 字段。
1. 展开 **[!UICONTROL Varnish Configuration]** 并输入以下信息：

   | 字段 | 描述 |
   | ----- | ----------- |
   | 访问列表 | 输入完全限定的主机名、IP地址或 [无类域间路由(CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) 表示法要使其内容失效的IP地址范围。 请参阅 [清漆缓存清除](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | 后端主机 | 输入Varnish的完全限定主机名或IP地址并监听端口 _后端_ 或 _原始服务器_；即，提供内容清漆的服务器将加速。 通常，这是您的Web服务器。 请参阅 [清漆缓存后端服务器](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | 后端端口 | 源服务器的侦听端口。 |
   | 宽限期 | 确定在后端无响应时，Varnish提供过时内容的时长。 默认值为300秒。 |
   | 处理参数大小  [!BADGE 2.4.7（测试版）]{type=Informative url="/help/release/release-notes/commerce/2-4-7.md" tooltip="仅在2.4.7 Beta版中提供"} | 指定最大数量 [布局句柄](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) 处理 [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) 用于全页缓存的HTTP端点。 限制大小可以提高安全性和性能。 默认值为100。 |

1. 单击 **保存配置**.

您还可以使用C命令行界面工具从命令行激活Varnish，而不是登录到Admin：

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## 导出Varnish配置文件

要从Admin导出Varnish配置文件：

1. 单击其中一个导出按钮以创建 `varnish.vcl` 你可以和清漆搭配使用。

   例如，如果您有Varnish 4，请单击 **为清漆4导出VCL**

   下图显示了一个示例：

   ![在管理员中配置Commerce以使用涂漆](../../assets/configuration/varnish-admin-22.png)

1. 备份您现有的 `default.vcl`. 然后重命名 `varnish.vcl` 您刚刚导出到的文件 `default.vcl`. 然后将文件复制到 `/etc/varnish/` 目录。

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe建议您打开 `default.vcl` 并更改 `acl purge` 到Varnish主机的IP地址。 （您可以在单独的行上指定多个主机，也可以使用CIDR表示法。）

   例如，

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. 如果要自定义Vagrant运行状况检查或宽限模式或saint模式配置，请参阅 [高级清漆配置](config-varnish-advanced.md).

1. 重新启动Varnish和您的Web服务器：

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 缓存静态文件

默认情况下，不应缓存静态文件，但如果要缓存它们，可以编辑部分 `Static files caching` 在VCL中具有以下内容：

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

在配置Commerce使用Varnish之前，您必须进行这些更改。
