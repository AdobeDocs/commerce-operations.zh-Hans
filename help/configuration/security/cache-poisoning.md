---
title: 防止缓存中毒
description: 了解如何防止您的Commerce店面出现页面缓存中毒。
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 防止缓存中毒

本主题讨论在使用Microsoft Internet Information Server (IIS) Web服务器时如何防止缓存中毒。 _缓存中毒_ 是一种更改缓存内容以包含来自同一站点的不同页面的方法。 例如，可以注入HTTP 404（未找到）错误页面来代替某些良性页面（例如，店面主页），这可能会导致潜在的拒绝服务(DoS)。 恶意页面URL由Varnish或Redis缓存，因此名称为 _页面缓存中毒_.

这些类型的攻击可能难以检测，因为它们不会导致Web服务器日志中出现错误。

此解决方案适用于以下Commerce版本：

- 2.0.10及更高版本
- 2.1.2及更高版本

>[!INFO]
>
>本主题适用于经验丰富的IIS管理员。

## 描述

如果在IIS服务器上启用了URL重写，并且在请求到达Varnish或Redis缓存服务之前更改了以下任何HTTP标头，则会导致此问题：

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

如果更改这些标头，则会缓存生成的URL和内容，从而导致潜在漏洞。

## 解决方案

我们提供相应选项，以根据 `Enable_IIS_Rewrites`.

- 如果 `Enable_IIS_Rewrites` 设置为 `0`，则标头的值将被删除。
- 如果 `Enable_IIS_Rewrites` 设置为 `1`，标头的值将保持不变。

>[!WARNING]
>
>如果您设置 `Enable_IIS_Rewrites` 到 `1`中，在请求到达IIS Web服务器之前，不得允许更改上述标头的值。
