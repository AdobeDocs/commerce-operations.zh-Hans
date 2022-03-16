---
title: Adobe Commerce性能优化
description: 通过更改某些默认设置，准备Adobe Commerce项目以将Adobe Experience Manager用作CMS。
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Adobe Commerce性能优化

## AEM和Adobe Commerce基础架构的地理位置

为了减少构建页面时AEM发布者与Adobe Commerce GraphQL之间的延迟，应在同一AWS（或Azure）区域内托管两个单独的基础结构的初始配置。 为这两个云选择的地理位置也应最接近大多数客户群，以便客户端GraphQL请求从地理位置上的较近位置提供给大多数客户。

## Adobe Commerce中的GraphQL缓存

当用户的浏览器或AEM发布者调用Adobe Commerce的GraphQL时，某些调用将以Fastly方式缓存。 缓存的查询通常是包含非个人数据且不太可能经常更改的查询。 例如：类别、类别列表和产品。 明确未缓存的是那些定期更改的，如果已缓存，则可能会对个人数据和网站操作（例如cart和customerPaymentTokens等查询）造成风险。

GraphQL允许您在一次调用中进行多个查询。 请务必注意，如果您甚至指定了一个查询，即Adobe Commerce没有将其他许多不可缓存的查询缓存在一起，Adobe Commerce将跳过调用中所有查询的缓存。 在合并多个查询时，开发人员应考虑这一点，以确保不会意外绕过可能缓存的查询‡。

>[!NOTE]
>
> 有关可缓存和不可缓存查询的更多信息，请参阅Adobe Commerce [开发人员文档](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## 目录平桌

不建议将平面表格用于产品和类别。 使用此已弃用的功能可能会导致性能下降和索引问题，因此应通过店面部分的Adobe Commerce管理员来禁用平面目录。 某些第三方模块和自定义确实需要平面表才能正常运行 — 建议进行评估，以了解在选择使用这些扩展或自定义时必须使用平面表所产生的影响和风险。

## 快源屏蔽

默认情况下，未启用Fastlyorigin屏蔽。 Fastly源屏蔽的目的是直接减少到Adobe Commerce源的流量：收到请求后，Fastlyedge位置（或“存在点”/POP）会检查是否存在缓存的内容并提供该内容。 如果未缓存，则会继续Shield POP检查其是否已缓存（如果先前已从其他全局POP请求内容，则会缓存）。 最后，如果未缓存在Shield POP上，则只会继续到源服务器。

可以在Adobe Commerce Admin Fast配置后端设置中启用FastlyOrigin屏蔽。 您应选择与Adobe Commerce原始数据中心最接近的屏蔽位置，以获得最佳性能。

## 快速图像优化

启用Fastlyorigin屏蔽后，您还可以激活Fastly Image Optimizer。 当产品目录图像存储在Adobe Commerce上时，此服务能够将所有资源密集型产品目录图像转换处理从Adobe Commerce源快速卸载到Fastly和Off。 由于图像在边缘位置被变换，通过减少返回到Adobe Commerce源的请求数来消除延迟，最终用户响应时间也因页面加载时间而缩短。

尽管只有在您的原始防护板被激活之后，才能在管理员的Fastly配置中通过“启用深层图像优化”来启用Fastly图像优化。 有关Fastly Image优化配置的更多详细信息，请参阅Adobe Commerce [开发人员文档](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html).

![Adobe Commerce管理员中Fastly图像优化设置的屏幕截图](../assets/commerce-at-scale/image-optimization.svg)

## 禁用未使用的模块

如果运行Adobe Commerce无头，则只会通过GraphQL端点来提供请求，而不会直接从Adobe Commerce提供任何前端存储页，则许多模块将变得冗余而不会使用。 通过禁用未使用的模块，您的Adobe Commerce代码库将变得更小、更简单，从而可以提高性能。 可以使用编辑器管理Adobe Commerce上的禁用模块。 哪些模块可以禁用取决于您网站的要求，因此无法提供推荐的列表，因为它将特定于每个客户的Adobe Commerce实施。

## MySQL和Redis连接激活

默认情况下，云上的Adobe Commerce中不会激活MySQL和Redis从连接。 这是因为这些设置仅适用于期望负载非常高的客户。 从连接激活后，跨可用区（跨可用区）延迟会更高，因此，如果实例仅接收常规负载级别，则此设置实际上会降低云实例上Adobe Commerce的性能。

如果Adobe Commerce实例需要极端负载，则激活MySQL和Redis的主控从程序将负载分散到不同节点，从而有助于提高性能。

作为指南，在负载正常的环境中，启用从连接会使性能降低10-15%。 但是，在负载和流量较大的群集上，性能提升约10-15%。 因此，务必使用预期流量级别来加载测试环境，以评估此设置是否对加载下的性能时间有益。

要启用/禁用mysql和redis的从连接，您应编辑 `.magento.env.yaml` 文件以包含以下内容：

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

对于缩放式架构（拆分式架构 — 请参阅下文），不应启用Redis从连接，因为这将导致显示错误。 对于拆分架构，建议为Redis实施L2缓存。

## 在云缩放（拆分）架构上迁移到Adobe Commerce

如果在完成上述所有配置后，加载测试结果或对实时基础架构性能的分析仍表明到Adobe Commerce的负载级别始终达到最大CPU和其他系统资源的级别，则应考虑迁移到缩放（拆分）架构。

使用标准Pro架构时，有3个节点，每个节点都包含完整的技术堆栈。 通过转换为分层架构，这最少更改为6个节点：其中包括Elasticsearch、MariaDB、Redis等核心服务；用于处理Web流量的其他3个包含phpfpm和NGINX。 分层存在更大的扩展可能性：包含数据库的核心节点可以垂直缩放；Web节点可以水平和垂直缩放，因此可以根据需要在设定的高负载活动期间和需要额外资源的节点上扩展基础架构，从而具有很大的灵活性。

如果由于对网站的负载期望过高而决定切换到分层架构，则应与客户成功经理讨论启用此功能的步骤。
