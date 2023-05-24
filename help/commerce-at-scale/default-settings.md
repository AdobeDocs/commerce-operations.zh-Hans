---
title: Adobe Commerce性能优化
description: 通过更改某些默认设置，准备您的Adobe Commerce项目以使用Adobe Experience Manager as a CMS。
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
source-git-commit: a11f3ef0519a4a6c08ea1d4e520ce0462e88885d
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Adobe Commerce性能优化

## AEM和Adobe Commerce基础架构的地理位置

为了减少AEM发布者与Adobe Commerce GraphQL在构建页面时的延迟，应在同一AWS（或Azure）区域内托管两个独立基础架构的初始配置。 为这两个云选择的地理位置也应该最接近您的大多数客户群，这样客户端GraphQL请求就可以从地理位置最接近您的大多数客户了。

## Adobe Commerce中的GraphQL缓存

当用户的浏览器或AEM发布者调用Adobe Commerce的GraphQL时，某些调用将缓存在Fastly中。 缓存的查询通常包含非个人数据并且不太可能经常更改。 例如：categories、categoryList和products。 明确未缓存的是定期更改的查询，如果缓存，可能会对个人数据和网站操作（例如查询购物车和customerPaymentTokens）带来风险。

GraphQL允许您在一次调用中进行多个查询。 请务必注意，如果您甚至指定一个查询，而Adobe Commerce不会与许多其他不可缓存的查询一起缓存，则Adobe Commerce将绕过调用中所有查询的缓存。 开发人员在合并多个查询时应考虑这一点，以确保不会无意中绕过潜在的可缓存查询‡。

>[!NOTE]
>
> 有关可缓存查询和不可缓存查询的更多信息，请参阅Adobe Commerce [开发人员文档](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## 目录平面表

不建议将平面表用于产品和类别。 使用此已弃用的功能可能会导致性能下降和索引问题，因此应通过Adobe Commerce管理员在店面部分中禁用平面目录。 某些第三方模块和自定义项确实需要平面表才能正常运行 — 建议进行评估以了解在选择使用这些扩展或自定义项时，与必须使用平面表相关的影响和风险。

## Fastly源屏蔽

默认情况下，不启用Fastly源屏蔽。 Fastly源屏蔽的目的是减少直接发往Adobe Commerce源的流量：当收到请求时，Fastly边缘位置（或“存在点”/POP）会检查缓存的内容并提供它。 如果未缓存，则继续访问Shield POP以检查是否缓存了内容（如果之前甚至从其他全局POP请求过内容，则会缓存）。 最后，如果未在Shield POP上缓存，则它只会继续到原始服务器。

可以在您的Adobe Commerce管理员Fastly配置后端设置中启用Fastly源屏蔽。 您应该选择最接近Adobe Commerce原始数据中心的屏蔽位置，以获得最佳性能。

## Fastly图像优化

启用Fastly源屏蔽后，您还可以激活Fastly图像优化器。 当产品目录图像存储在Adobe Commerce上时，该服务能够将所有资源密集型产品目录图像转换处理卸载到Fastly上，并从Adobe Commerce源中卸载。 由于图像在边缘位置转换，最终用户的响应时间也因页面加载时间而得以改进，这通过减少返回Adobe Commerce原点的请求数来消除延迟。

Fastly图像优化可以通过在Admin中的Fastly配置中“启用深层图像优化”来启用，但前提是您的原始防护板已激活。 有关用于Fastly图像优化的配置的更多详细信息，请参阅Adobe Commerce [开发人员文档](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html).

![Adobe Commerce管理员中Fastly图像优化设置的屏幕截图](../assets/commerce-at-scale/image-optimization.svg)

## 禁用未使用的模块

如果运行Adobe Commerce Headless，则只有通过GraphQL端点服务请求，而没有直接从Adobe Commerce提供前端商店页面，因此许多模块会变得冗余并且无法使用。 通过禁用未使用的模块，您的Adobe Commerce代码库会变得更小、更不复杂，因此可以提供性能改进。 可使用Composer管理Adobe Commerce上的禁用模块。 哪些模块可以禁用取决于您的网站要求，因此不会提供推荐列表，因为它将特定于每个客户的Adobe Commerce实施。

## MySQL和Redis连接激活

默认情况下，云上的Adobe Commerce中不激活MySQL和Redis从属连接。 这是因为这些设置仅适用于预期负载非常高的客户。 在从属连接激活时，跨可用区（跨可用区）延迟较高，因此，在实例仅接收常规负载级别的情况下，此设置实际上会降低Adobe Commerce在云实例上的性能。

如果Adobe Commerce实例预期负载极大，则为MySQL和Redis激活主控从节点可通过将MySQL数据库或Redis上的负载分散到不同的节点来帮助提高性能。

作为指导，在负载正常的环境中，启用从属连接将使性能降低10-15%。 但在负载和流量较大的群集上，性能提升大约10-15%。 因此，使用预期的流量级别对您的环境进行负载测试，以评估此设置是否对负载下的性能时间有益，这一点很重要。

要启用/禁用mysql和redis的从属连接，您应该编辑 `.magento.env.yaml` 文件，以包含以下内容：

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

对于缩放架构（拆分架构 — 见下文），不应启用Redis从属连接，因为这将导致显示错误。 在拆分架构的情况下，建议为Redis实施L2缓存。

## 迁移到云上扩展（拆分）架构的Adobe Commerce

如果在执行完上述所有配置后，负载测试结果或实时基础架构性能分析仍表明Adobe Commerce的负载级别始终充满CPU和其他系统资源，则应考虑迁移到扩展（拆分）架构。

在标准Pro体系结构中，有3个节点，每个节点都包含一个完整的技术栈栈。 通过转换为分割层架构，这将至少更改为6个节点：其中3个包含Elasticsearch、MariaDB、Redis和其他核心服务；其他3个用于处理Web流量的节点包含phpfpm和NGINX。 使用拆分层扩展的可能性更大：包含数据库的核心节点可以垂直扩展；Web节点可以水平或垂直扩展，从而提供很大的灵活性，可以根据需要扩展基础架构，以满足设定的高负载活动周期以及需要额外资源的节点上的需要。

如果由于网站负载要求较高而决定切换到分层架构，则应与Adobe客户团队讨论启用此架构的步骤。
