---
title: 防止点击劫持攻击
description: 通过使用“X-Frame-Options”标头控制页面渲染来阻止点击劫持攻击。
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
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
source-wordcount: '234'
ht-degree: 0%
---
# 防止点击劫持攻击

通过在店面的请求中包含[X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) HTTP请求标头，防止[点击劫持](https://owasp.org/www-community/attacks/Clickjacking)攻击。

`X-Frame-Options`标题允许您指定是否允许浏览器在`<frame>`、`<iframe>`或`<object>`中呈现页面，如下所示：

- `DENY`：页面无法显示在框架中。
- `SAMEORIGIN`：（默认）页面只能在与页面本身同源的框架中显示。

>[!WARNING]
>
>`ALLOW-FROM <uri>`选项已被弃用，因为Commerce支持的浏览器不再支持它。 查看[浏览器兼容性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility)。

>[!WARNING]
>
>出于安全原因，Adobe强烈建议不要在框架中运行Commerce店面。

## 实施`X-Frame-Options`

在`<project-root>/app/etc/env.php`中设置`X-Frame-Options`的值。 缺省值设置如下：

```php
'x-frame-options' => 'SAMEORIGIN',
```

重新部署以使对`env.php`文件所做的任何更改生效。

>[!TIP]
>
>编辑`env.php`文件比在管理员中设置值更安全。

## 验证`X-Frame-Options`的设置

要验证您的设置，请查看任何店面页面上的HTTP标头。 可通过多种方法做到这一点，包括使用Web浏览器检查器。

以下示例使用curl，您可以从任何可以通过HTTP协议连接到Commerce服务器的计算机运行它。

```shell
curl -I -v --location-trusted '<storefront-URL>'
```

在标头中查找`X-Frame-Options`值。
