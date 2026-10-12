---
title: 防止缓存中毒
description: 了解如何防止您的Commerce店面出现页面缓存中毒。
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%
---
# 防止缓存中毒

本主题讨论在使用Microsoft Internet Information Server (IIS) Web服务器时如何防止缓存中毒。 _缓存中毒_&#x200B;是一种将缓存内容更改为包含来自同一站点的不同页面的方法。 例如，可以注入HTTP 404（未找到）错误页面来代替某些良性的页面（例如，店面主页），这可能导致潜在的拒绝服务(DoS)。 恶意页面URL由Varnish或Redis缓存，因此名称为&#x200B;_页面缓存中毒_。

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

如果更改这些标头，则生成的URL和内容将缓存，从而导致潜在漏洞。

## 解决方案

我们提供了根据`Enable_IIS_Rewrites`的IIS服务器设置删除所有上述标头的值的选项。

- 如果`Enable_IIS_Rewrites`设置为`0`，则标头的值将被删除。
- 如果`Enable_IIS_Rewrites`设置为`1`，则标头的值将保持不变。

>[!WARNING]
>
>如果将`Enable_IIS_Rewrites`设置为`1`，则在请求到达IIS Web服务器之前，不能允许更改上述标头的值。
