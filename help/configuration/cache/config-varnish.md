---
title: 配置和使用清漆
description: 了解Varnish如何存储文件并改进HTTP流量。
feature: Configuration, Cache
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---

# 配置清漆

[清漆缓存]是开源Web应用程序加速器（也称为&#x200B;_HTTP加速器_&#x200B;或&#x200B;_缓存HTTP反向代理_）。 Varnish在内存中存储（或缓存）文件或文件片段，从而使Varnish能够减少未来对等请求的响应时间和网络带宽消耗。 与Apache和nginx等Web服务器不同，Varnish专为HTTP协议而设计。

[系统要求](../../installation/system-requirements.md)列出了支持的Varnish版本。

>[!WARNING]
>
>我们&#x200B;_强烈建议_&#x200B;您在生产中使用清漆。 对于文件系统或[数据库](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)的内置全页缓存比Varnish慢得多，而Varnish旨在加速HTTP流量。

有关Varnish的详细信息，请参阅：

- [大型涂漆图片]
- [清漆启动选项]
- [涂漆和网站性能]

## 清漆拓扑图

下图显示了Commerce拓扑中Varnish的基本视图。

![基本清漆图](../../assets/configuration/varnish-basic.png)

在上图中，用户通过Internet发出的HTTP请求会导致CSS、HTML、JavaScript和图像的大量请求（统称为&#x200B;_资源_）。 清漆位于Web服务器前面，并将这些请求代理到Web服务器。

在Web服务器返回资产时，可缓存的资产存储在Varnish中。 随后对这些资产的任何请求均由Varnish执行（即，请求不会到达Web服务器）。 清漆可以非常快速地返回缓存的内容。 这样可以缩短将内容返回给用户的响应时间，减少Commerce必须完成的请求数。

由Varnish缓存的Assets以可配置间隔过期，或被相同资源的较新版本替换。 您还可以使用Admin或[`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)命令手动清除缓存。

## 流程概述

本主题讨论如何以最少的参数集初始安装Varnish并测试其是否正常工作。 然后，从Commerce管理员导出清漆配置并再次进行测试。

该过程可概括如下：

1. 安装Varnish并通过访问任何Commerce页面对其进行测试，以查看是否获得指示Varnish正在工作的HTTP响应标头。
1. 安装Commerce软件并使用管理员创建Varnish配置文件。
1. 将您现有的Varnish配置文件替换为Admin生成的配置文件。
1. 再次测试所有内容。

   如果`<magento_root>/var/page_cache`目录中没有任何内容，则表示您已成功使用Commerce配置清漆！

>[!NOTE]
>
>- 除了上面提到的以外，您必须以具有`root`权限的用户身份输入本主题中讨论的所有命令。
>
>- 本主题为CentOS和Apache 2.4上的Varnish编写。如果在不同的环境中设置“清漆”，某些命令可能会不同。 有关更多信息，请参阅Varnish文档。

## 已知问题

我们知道以下与Varnish有关的问题：

- [清漆不支持SSL]

  作为替代方法，请使用SSL终止或SSL终止代理。

- 如果手动删除`<magento_root>/var/cache`目录的内容，则必须重新启动Varnish。

- 安装Commerce时可能出错：

  ```terminal
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

## 清漆缓存概述

清漆缓存可使用以下方式与Commerce配合使用：

- Magento2 GitHub存储库中的[`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)
- Commerce提供的Apache的`.htaccess`分布式配置文件
- 使用[管理员](../cache/configure-varnish-commerce.md)生成的清漆的`default.vcl`配置

>[!INFO]
>
>本主题仅介绍上述列表中的默认选项。 在复杂情况下可使用许多其他方法配置缓存（例如，使用内容交付网络）；这些方法不在本指南的涵盖范围内。

在第一次浏览器请求时，可缓存的资产会从Varnish提交到客户端浏览器，并缓存在浏览器上。

此外，Varnish将实体标记(ETag)用于静态资产。 通过ETag可以确定静态文件在服务器上的更改时间。 因此，当静态资产在服务器上发生更改时（根据来自浏览器的新请求或客户端刷新浏览器缓存时，通常通过按F5或Control+F5），这些资产将被发送到客户端。

以下各节将提供更多详细信息。

## 按浏览器请求缓存

此部分使用浏览器检查器来显示如何在第一个请求中将资产传递到浏览器，以及之后如何从本地浏览器缓存加载资产。

### 第一个浏览器请求

`nginx.conf.sample`和`.htaccess`提供了客户端缓存选项。 当浏览器第一次请求可缓存对象时，Varnish会将其提供给客户端。

下图显示了使用浏览器检查器的示例：

![首次请求可缓存对象时，Varnish会将其提供给浏览器](../../assets/configuration/varnish-apache-first-visit.png)

上例显示了storefront主页面(`m2_ce_my`)的请求。 CSS和JavaScript资源缓存在客户端浏览器中。

>[!NOTE]
>
>大多数静态资产都有一个HTTP 200 (OK)状态代码，表示资产是从服务器检索的。

### 第二次浏览器请求

如果同一浏览器再次请求同一页面，则这些资产将从本地浏览器缓存中交付，如下图所示。

![下次请求同一对象时，从本地浏览器缓存加载资源](../../assets/configuration/varnish-apache-second-visit.png)

请注意第一个请求和第二个请求之间的响应时间差异。 同样，静态资产具有200 (OK)响应代码，因为它们是首次从本地缓存中交付。

## Commerce如何使用Etag

以下示例显示特定静态资源的响应标头。

![通过ETag，可以更轻松地确定静态资源是否已更改](../../assets/configuration/varnish-etag.png)

`calendar.css`具有ETag响应标头，这意味着客户端浏览器上的CSS文件可以与服务器上的文件进行比较。

此外，静态资产会以304（未修改）HTTP状态代码返回，如下图所示。

![HTTP 304 （未修改）响应代码指示本地缓存中的静态资源与服务器上的相同](../../assets/configuration/varnish-304.png)

出现304状态代码是因为用户使其本地缓存失效，并且服务器上的内容未发生更改。 由于304状态代码，静态资源&#x200B;_内容_&#x200B;未传输；只将HTTP标头下载到浏览器。

如果服务器上的内容发生更改，则客户端将下载静态资产，其中包含HTTP 200 (OK)状态代码和新的ETag。

<!-- Link Definitions -->

[亮光的大图片]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[清漆缓存]: https://varnish-cache.org
[清漆启动选项]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[涂漆和网站性能]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[清漆不支持SSL]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
