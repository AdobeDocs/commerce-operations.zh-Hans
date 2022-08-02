---
title: 配置和使用清漆
description: 了解清漆如何存储文件并改进HTTP流量。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---


# 配置清漆

[清漆缓存] 是开源web应用程序加速器(也称为 _HTTP加速器_ 或 _缓存HTTP反向代理_)。 清漆可将文件或文件片段存储（或缓存）到内存中，这样，清漆可减少未来等效请求的响应时间和网络带宽消耗。 与Apache和nginx等Web服务器不同，Imest专门与HTTP协议一起使用。

Commerce 2.4.2使用清漆6.4进行测试。 Commerce 2.4.x与清漆6.x兼容

>[!WARNING]
>
>我们 _强烈建议_ 你在生产中用清漆。 内置的全页缓存 — 用于文件系统或 [数据库] — 比Quiste速度要慢得多，并且Quiste旨在加速HTTP流量。

有关清漆的详细信息，请参阅：

- [大清漆画]
- [清漆启动选项]
- [清漆和网站性能]

## 清漆拓扑图

下图显示了Commerce拓扑中Rikest的基本视图。

![基本清漆图](../../assets/configuration/varnish-basic.png)

在上图中，用户通过Internet发出的HTTP请求会导致对CSS、HTML、JavaScript和图像(统称为 _资产_)。 清漆位于Web服务器之前，并将这些请求代理给Web服务器。

当Web服务器返回资产时，可缓存的资产将存储在清漆中。 这些资产的任何后续请求都将通过清漆（这意味着请求不会到达Web服务器）来完成。 清漆可以极快地返回缓存的内容。 结果是，将内容返回给用户的响应时间更快，并且商务必须满足的请求数量也减少了。

通过清漆缓存的资产会以可配置的间隔过期，或者会被相同资产的较新版本所替换。 您还可以使用 [管理员](https://glossary.magento.com/magento-admin) 或 [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令。

## 流程概述

本主题讨论如何在初始安装Rimeth时使用最少的一组参数并测试其是否有效。 然后，从商务管理员中导出清漆配置，并再次进行测试。

该过程可概括如下：

1. 安装清漆并通过访问任何商务页面来测试清漆，以查看您是否收到指示清漆工作的HTTP响应标头。
1. 安装商务软件，然后使用管理员创建清漆配置文件。
1. 将现有的清漆配置文件替换为由管理员生成的配置文件。
1. 再测试一切。

   如果 `<magento_root>/var/page_cache` 目录中，您已成功配置了商务清漆！

>[!NOTE]
- 除非另有说明，否则您必须以用户身份输入本主题中讨论的所有命令 `root` 权限。
- 本主题是为CentOS和Apache 2.4上的清漆编写的。如果您在其他环境中设置清漆，则某些命令可能会有所不同。 有关更多信息，请参阅清漆文档。


## 已知问题

我们知道清漆存在以下问题：

- [清漆不支持SSL]

   作为替代方法，请使用SSL终止或SSL终止代理。

- 如果手动删除 `<magento_root>/var/cache` 目录，必须重新启动清漆。

- 安装商务时可能出错：

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

## 清漆缓存概述

清漆缓存适用于Commerce:

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) 从Magento2 GitHub存储库
- `.htaccess` Commerce提供的Apache的分布式配置文件
- `default.vcl` 使用生成的清漆的配置 [管理员](../cache/config-varnish-magento.md)

>[!INFO]
本主题仅涵盖上一列表中的默认选项。 在复杂情景中，有许多其他方法可配置缓存（例如，使用内容交付网络）；这些方法不在本指南的范围之内。

在第一个浏览器请求中，可缓存的资产会从清漆传送到客户端浏览器，并缓存在浏览器上。

此外，清漆使用 [实体](https://glossary.magento.com/entity) 静态资产的标记(ETag)。 ETag提供了确定何时 [静态文件](https://glossary.magento.com/static-files) 更改服务器。 因此，静态资产在服务器上发生更改时（无论是在来自浏览器的新请求中，还是在客户端刷新浏览器缓存时），都会发送给客户端，通常是按F5或Control+F5。

以下各节提供了更多详细信息。

## 按浏览器请求缓存

此部分使用浏览器检查器来显示如何在第一次请求中以及随后从本地浏览器缓存加载资产时将资产交付到浏览器。

### 第一个浏览器请求

`nginx.conf.sample` 和 `.htaccess` 提供客户端缓存选项。 当从浏览器对可缓存对象发出第一个请求时，清漆会将请求传送到客户端。

下图显示了使用浏览器检查器的示例：

![第一次对可缓存对象提出请求时，清漆会将请求传送到浏览器](../../assets/configuration/varnish-apache-first-visit.png)

上例显示了对storefront主页(`m2_ce_my`)。 CSS和JavaScript资产会在客户端浏览器上缓存。

>[!NOTE]
大多数静态资产都具有HTTP 200（确定）状态代码，表示是从服务器中检索资产。

### 第二个浏览器请求

如果同一浏览器再次请求同一页面，则这些资产会从本地浏览器缓存中交付，如下图所示。

![下次请求同一对象时，将从本地浏览器缓存中加载资产](../../assets/configuration/varnish-apache-second-visit.png)

请注意第一个请求和第二个请求之间响应时间的差异。 同样，静态资产具有200(OK)响应代码，因为这是首次从本地缓存中交付响应代码。

## 商务如何使用Etag

以下示例显示特定静态资产的响应标头。

![ETag可更轻松地确定静态资产是否已更改](../../assets/configuration/varnish-etag.png)

`calendar.css` 具有ETag响应标头，这意味着可以将客户端浏览器上的CSS文件与服务器上的CSS文件进行比较。

此外，会使用304（未修改）HTTP状态代码返回静态资产，如下图所示。

![HTTP 304（未修改）响应代码指示本地缓存中的静态资产与服务器上的静态资产相同](../../assets/configuration/varnish-304.png)

出现304状态代码是因为用户使其本地缓存失效，并且服务器上的内容没有更改。 由于状态代码为304，因此该静态资产 _内容_ 未转让；只有HTTP头会下载到浏览器。

如果服务器上的内容发生更改，客户端将下载具有HTTP 200（确定）状态代码和新ETag的静态资产。

<!-- Link Definitions -->

[数据库]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/cache/partial-caching/database-caching.html
[大清漆画]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[清漆缓存]: https://varnish-cache.org
[清漆启动选项]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[清漆和网站性能]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[清漆不支持SSL]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
