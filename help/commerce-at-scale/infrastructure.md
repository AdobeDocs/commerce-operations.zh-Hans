---
title: Adobe Commerce和Adobe Experience Manager基础架构协调
description: 调整您的Adobe Commerce和Adobe Experience Manager基础架构，以设置可接受的超时和连接限制。
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# 基础架构对齐（超时和连接限制）

AEM和Adobe Commerce以及周围的基础架构（如负载平衡器）中有一些设置需要协调，这些设置与连接限制和超时设置相关。

这些限制之间的未对齐将意味着连接最终可能会在AEM侧被限制，而Adobe Commerce能够处理更多连接。 同样，对于超时设置，如果未对齐，则可能意味着在Adobe Commerce仍在处理请求时，AEM端出现超时错误。

对于超时设置，应审核并调整设置，以防止在加载下出现503超时错误。 需要查看以下几个基础架构和应用程序超时设置：

![描述AEM超时和连接限制的编号图](../assets/commerce-at-scale/timeout-settings.svg)

## AEM负载平衡器

假设基础架构中有一个AWS应用程序负载平衡器和多个调度程序/发布程序，则应考虑负载平衡器的以下设置：

1. 应审查发布程序运行状况检查，以防止调度程序在不必要的早期停止服务，以免出现负载电涌。 负载平衡器运行状况检查的超时设置应与发布者超时设置保持一致。

   ![显示AEM负载平衡器运行状况检查的屏幕截图](../assets/commerce-at-scale/health-checks.png)

1. 可以禁用调度程序目标组吸引力，并且可以使用轮循负载平衡算法。 这是假设没有AEM特定功能或AEM用户会话需要设置会话吸引力。 本指南假定用户登录和会话管理仅通过GraphQL在Adobe Commerce上运行。

   ![显示AEM会话粘性属性的屏幕截图](../assets/commerce-at-scale/session-stickiness.png)

1. 请注意，如果您启用了会话粘性，这可能会导致请求无法快速缓存，因为默认情况下，Fastly不会使用Set-Cookie标头来缓存页面。 Adobe Commerce即使在可缓存页面上(TTL > 0)也会设置Cookie，但默认的Fastly VCL会删除可缓存页面上的这些Cookie，以便快速缓存正常工作。 如果页面没有缓存，请检查您可能使用的任何自定义Cookie，并上传Fastly VCL并重新检查网站。

## 调度程序超时设置

调度程序“renders”选项中的/timeout以毫秒为单位指定访问AEM发布实例的连接超时。 如果存在单独的负载平衡器来处理超时设置，则应该对此进行审核，并使用默认设置“0”（无限超时）。

如果基础结构中没有负载平衡器，则应在调度程序/超时设置中指定超时设置，其值应与发布程序中的GraphQL超时设置匹配。

## 发布者

发布者GraphQL连接限制和超时：最初，应将Adobe Commerce CIF GraphQL客户端配置工厂OSGI中的Max HTTP连接数设置设置为默认的Fastly最大连接数限制，该限制当前设置为200。 即使AEM场中存在多个发布者，每个发布者的限制也应设置为相同，并与“Fastly”（快速）设置相匹配。 其原因在于，在某些情况下，如果将关联的调度程序从场中取出，则一个发布者处理的流量可能比其他发布者多。 这意味着所有流量都将通过剩余的单个调度程序和发布程序进行路由，在这种情况下，单个发布程序可能需要所有HTTP连接。

“默认HTTP方法”应从POST设置为GET。 只有GET请求会缓存在Adobe Commerce GraphQL缓存中，因此默认方法应始终设置为GET。

应将http连接超时和http套接字超时设置为与Fastlytimeout匹配的值。

下图显示了MagentoCIF GraphQL客户端配置工厂。 此处显示的设置仅是示例，需要逐个调整：

![商务集成框架配置设置屏幕截图](../assets/commerce-at-scale/cif-config.png)

下图显示了Fastly后端配置。 此处显示的设置仅是示例，需要逐个调整：

![Fastly的“商务管理员”配置设置屏幕截图](../assets/commerce-at-scale/cif-config-advanced.png)
