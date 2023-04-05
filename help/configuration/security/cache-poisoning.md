---
title: 防止缓存中毒
description: 了解如何防止Commerce店面的页面缓存中毒。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# 防止缓存中毒

本主题讨论在使用Microsoft Internet Information Server(IIS)Web服务器时如何防止缓存中毒。 _缓存中毒_ 是一种更改缓存内容以包含来自同一站点的不同页面的方法。 例如，可以插入HTTP 404（未找到）错误页面来代替某些良性页面（例如，店面主页），这可能会导致潜在的拒绝服务(DoS)。 恶意页面URL被Rikest或Redis缓存，因此名称 _页面缓存中毒_.

这些类型的攻击可能很难检测，因为它们不会导致Web服务器日志中的错误。

此解决方案适用于以下商务版本：

- 2.0.10及更高版本
- 2.1.2及更高版本

>[!INFO]
>
>本主题面向经验丰富的IIS管理员。

## 描述

如果IIS服务器上启用了URL重写，并且在请求到达Hise或Redis缓存服务之前更改了以下任何HTTP标头，则会导致该问题：

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

如果更改了这些标头，则会缓存生成的URL和内容，从而导致潜在的漏洞。

## 解决方案

我们提供了一个选项，用于根据 `Enable_IIS_Rewrites`.

- 如果 `Enable_IIS_Rewrites` 设置为 `0`，则会删除标头的值。
- 如果 `Enable_IIS_Rewrites` 设置为 `1`，则标题的值将保持不变。

>[!WARNING]
>
>如果设置 `Enable_IIS_Rewrites` to `1`，则不得在请求到达IIS Web服务器之前更改上述标头的值。
