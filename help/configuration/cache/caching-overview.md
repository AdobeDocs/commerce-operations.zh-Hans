---
title: 缓存概述和配置选项
description: 了解Adobe Commerce中的缓存，包括后端存储、前端配置以及使用Varnish、Redis、Valkey和L2缓存的全页缓存。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 9cd0f2a84772e2d68fd15a00651216abfa9ec91c
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# 缓存概述和配置选项

Adobe Commerce依靠多层缓存体系结构来减少数据库负载，最大程度地减少冗余处理，并加快页面交付。 在应用程序级别，Commerce维护十几种[缓存类型](../cli/manage-cache.md#clean-and-flush-cache-types)，如配置、布局、块HTML和集合，每种类型都可以路由到专用存储后端，如[Redis](config-redis.md)或[Valkey](config-valkey.md)。 对于全页缓存，Adobe强烈建议使用[Varnish](config-varnish.md)，它是一个HTTP加速器，直接从内存提供缓存的页面。 其他层（如[L2缓存](level-two-cache.md)和[静态内容签名](static-content-signing.md)）可进一步提高高流量、多节点部署的性能。

本指南将介绍每个缓存层的工作方式，并展示如何配置前端、后端和高级选项以满足您的部署要求。

## 缓存前端

缓存前端是Commerce和缓存存储后端之间的接口。 您可以定义多个前端，每个前端具有不同的后端设置，然后为每个前端分配特定的[缓存类型](../cli/manage-cache.md#clean-and-flush-cache-types)。  有关配置详细信息，请参阅[配置缓存前端](cache-types.md)。

## 缓存后端

缓存后端是缓存数据的底层存储机制。 Commerce提供默认的文件系统后端，但您可以配置其他后端，如Redis或Valkey，以提高性能和可扩展性。 有关可用选项的详细信息，请参阅[缓存后端选项](cache-options.md)。

## 使用Varnish的全页缓存

[Varnish缓存](config-varnish.md)是一个HTTP加速器，在内存中缓存完整的页。 Adobe强烈建议在生产环境中使用Varnish，因为它比内置全页缓存快得多。

>[!NOTE]
>
>清漆作为Web服务器前面的反向代理运行，不需要更改Commerce缓存后端配置。

## L2（两级）缓存

[二级缓存](level-two-cache.md)使用远程缓存（Redis或Valkey）作为真实来源时，将缓存数据本地存储在每个Web节点上。 这可以减少Web节点与远程缓存之间的网络流量，从而提高高流量站点的性能。

## 静态内容缓存

[静态内容签名](static-content-signing.md)通过在文件URL中嵌入部署版本，使静态资源（CSS、JavaScript、图像）的浏览器缓存失效。

## 缓存术语

[!DNL Commerce]使用以下缓存术语：

- **前端** — 缓存存储的接口或网关，由[Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend)实现。
- **缓存类型** — 随[!DNL Commerce]提供的内置类型之一（如`config`、`layout`、`block_html`、`full_page`）或[自定义类型](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/)。
- **后端** — 指定由[Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)实现的[缓存存储](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)的详细信息。
- **二级后端** — 将缓存记录存储在两个后端中：本地（快速）缓存和远程（共享）缓存。 请参阅[二级缓存配置](level-two-cache.md)。

## 配置选项

缓存配置存储在两个文件中：

- `<magento_root>/app/etc/di.xml` — 全局依赖项注入配置。 修改此文件以更改提供的`default`缓存前端。
- `<magento_root>/app/etc/env.php` — 特定于环境的配置。 修改此文件以配置自定义缓存前端。 此文件覆盖`di.xml`中的等效配置。

有关前端到类型映射和缓存配置语法的详细信息，请参阅：

- [配置缓存前端](cache-types.md) — 将缓存前端与特定缓存类型关联
- [缓存后端选项](cache-options.md) — 后端选项引用
