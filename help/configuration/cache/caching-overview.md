---
title: 缓存概述和配置选项
description: 了解Adobe Commerce中的缓存，包括后端存储、前端配置以及使用Varnish、Redis、Valkey和L2缓存的全页缓存。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# 缓存概述和配置选项

Adobe Commerce使用多个缓存层来减少重复处理，降低数据库负载，并缩短响应时间。 这些层在请求和资产投放的不同时间点运行：

- **应用程序缓存**&#x200B;存储使用Commerce缓存类型生成或处理的数据。
- **HTTP全页缓存**&#x200B;在到达Commerce应用程序之前存储完整的HTTP响应。
- **二级缓存**&#x200B;可以在共享远程缓存存储之前的每个Web节点上添加本地缓存。
- **静态内容缓存**&#x200B;允许浏览器重用CSS、JavaScript、图像和其他静态资源。

本页提供了这些层的概念性概述以及指向其配置指导的链接。 有关后端选项、实施详细信息和特定于版本的设置，请参阅[缓存后端选项和存储引用](cache-options.md)。

## 缓存层

### 应用程序缓存

Commerce应用程序缓存的组织方式如下：

>[!BEGINSHADEBOX]

缓存类型→缓存前端→缓存后端

>[!ENDSHADEBOX]

**缓存类型**&#x200B;标识要缓存的数据类型，如配置、布局、块HTML或全页内容。 **缓存前端**&#x200B;将一个或多个缓存类型连接到存储。 **缓存后端**&#x200B;提供存储实现。

当需要单独的缓存设置或存储时，可以将不同的缓存类型分配给不同的前端。 有关配置详细信息，请参阅[配置缓存前端和类型](cache-types.md)。

### 整页HTTP缓存

HTTP全页缓存会在HTTP或CDN层存储完整的响应。 对于生产部署：

- **Adobe Commerce本地**—Adobe建议使用[Varnish](config-varnish.md)进行全页缓存。 Varnish在Web服务器前面充当反向代理。
- 云基础架构上的&#x200B;**Adobe Commerce**&#x200B;使用[Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly){target="_blank"}作为边缘缓存层和全页缓存层。 云基础架构不使用单独管理的清漆服务。

>[!NOTE]
>
>更改Commerce应用程序缓存后端不会配置Varnish或Fastly。 全页HTTP缓存与低级应用程序缓存分开配置和管理。

### L2缓存

二级缓存（即两级缓存）在每个Commerce Web节点上添加一个本地缓存，同时保留共享的远程缓存存储。 频繁访问的数据可以在本地提供，从而减少在多节点部署中与远程缓存的通信。

L2配置和支持的实施因Commerce版本和部署类型而异。 有关详细信息，请参阅[二级缓存配置](level-two-cache.md)。

### 静态内容缓存

Commerce可以通过向静态资源（如CSS、JavaScript和图像）的URL添加部署版本来改进其浏览器缓存。 内容更改时，URL会发生变化，导致浏览器请求新资源，而不是使用旧版缓存副本。

## 特定于部署的配置

以下配置任务因部署类型而异。

| 任务 | 内部部署 | 云基础架构 |
| --- | --- | --- |
| 应用程序缓存后端 | [缓存后端选项和存储引用](cache-options.md) | [Valkey和Redis服务配置的最佳实践](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md) |
| HTTP全页缓存 | [配置清漆](config-varnish.md) | [Fastly服务概述](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) |

以下任务适用于所有部署类型：

- **配置缓存类型和前端** [配置缓存前端和类型](cache-types.md)以将缓存类型与缓存前端相关联。
- **配置二级缓存**—[二级缓存配置](level-two-cache.md)。
- **为静态内容配置浏览器缓存失效**—[静态内容签名和浏览器缓存失效](static-content-signing.md)。
