---
title: Adobe Commerce和Adobe Experience Manager基础架构协调
description: 调整您的Adobe Commerce和Adobe Experience Manager基础架构，以设置可接受的超时和连接限制。
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# 基础架构调整（超时和连接限制）

有些设置与AEM和Adobe Commerce以及周围的基础架构（如负载平衡器）需要保持一致，这些设置与连接限制和超时设置有关。

这些限制之间的不一致意味着连接最终可能会在AEM端被限制，而Adobe Commerce能够处理更多连接。 同样，对于超时设置，未对齐可能意味着AEM端发生超时错误，而Adobe Commerce仍在处理请求。

对于超时设置，应查看设置并对齐，以防止在加载下出现503超时错误。 有几个基础架构和应用程序超时设置需要审查：

![描述AEM超时和连接限制的编号图表](../assets/commerce-at-scale/timeout-settings.svg)

## AEM负载平衡器

假设基础架构中有一个AWS应用程序负载平衡器和多个Dispatcher/发布者 — 应考虑对负载平衡器进行以下设置：

1. 应审查发布服务器运行状况检查，以防止Dispatcher过早地退出服务，避免负载激增。 负载平衡器运行状况检查的超时设置应与发布服务器超时设置一致。

   ![显示AEM负载平衡器运行状况检查的屏幕快照](../assets/commerce-at-scale/health-checks.png)

1. 可以禁用Dispatcher目标组粘性，并且可以使用Round Robin负载平衡算法。 这是假设没有使用需要设置会话粘性的AEM特定功能或AEM用户会话。 它假定用户登录和会话管理仅通过GraphQL在Adobe Commerce上进行。

   ![显示AEM会话粘性属性的屏幕快照](../assets/commerce-at-scale/session-stickiness.png)

1. 请注意，如果您启用了会话粘性，这可能会导致不缓存Fastly请求，因为默认情况下，Fastly不会使用Set-Cookie标头缓存页面。 Adobe Commerce甚至可以在可缓存页面上设置Cookie(TTL > 0)，但默认的Fastly VCL会删除可缓存页面上的这些Cookie，以便Fastly缓存正常工作。 如果页面未缓存，请检查您可能使用的任何自定义Cookie，还可上传Fastly VCL并重新检查站点。

## Dispatcher超时设置

Dispatcher“renders”选项中的/timeout指定访问AEM发布实例的连接超时（以毫秒为单位）。 应查看此项，如果存在单独的负载平衡器来处理超时设置，则应使用默认设置“0”（无限超时）。

如果基础结构中没有负载平衡器，则应在Dispatcher /timeout设置中指定超时设置，并且其值与发布服务器中的GraphQL超时设置匹配。

## 发布者

发布者GraphQL连接限制和超时：最初，Adobe Commerce CIF GraphQL客户端配置工厂OSGI中的最大HTTP连接数应设置为默认的Fastly最大连接数限制，当前设置为200。 即使AEM场中有多个发布者，也应针对每个发布者将限制设置为相同，并匹配Fastly设置。 原因在于，在某些情况下，例如，如果从场中取出关联的Dispatcher，则一个发布者可能会处理比其他发布者更多的流量。 这意味着所有流量都将通过剩余的单个Dispatcher和发布者路由，在这种情况下，单个发布者可能需要所有HTTP连接。

应将“默认HTTP方法”从POST设置为GET。 Adobe Commerce GraphQL缓存中仅缓存GET请求，因此默认方法应始终设置为GET。

应将http连接超时和http套接字超时设置为与Fastly超时匹配的值。

下图显示了MagentoCIF GraphQL Client Configuration Factory。 此处显示的设置仅为示例，需要根据具体情况进行调整：

![Commerce集成框架配置设置的屏幕截图](../assets/commerce-at-scale/cif-config.png)

下图显示了Fastly后端配置。 此处显示的设置仅为示例，需要根据具体情况进行调整：

![Fastly的Commerce管理员配置设置屏幕截图](../assets/commerce-at-scale/cif-config-advanced.png)
