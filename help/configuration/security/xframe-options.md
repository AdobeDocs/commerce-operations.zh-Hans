---
title: X-Frame-Options标头
description: 使用X-Frame-Options控制页面渲染。
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# X-Frame-Options标头

帮助防止 [点击劫持](https://owasp.org/www-community/attacks/Clickjacking) 利用漏洞，我们添加了一个选项来使用 [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) 请求中的HTTP请求标头。

此 `X-Frame-Options` 标头允许您指定是否允许浏览器在中呈现页面 `<frame>`， `<iframe>`，或 `<object>` 如下所示：

- `DENY`：页面无法显示在框架中。
- `SAMEORIGIN`：（默认）页面只能在与页面本身同源的框架中显示。

>[!WARNING]
>
>此 `ALLOW-FROM <uri>` 选项已被弃用，因为受Commerce支持的浏览器不再支持它。 请参阅 [浏览器兼容性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>出于安全原因，Adobe强烈建议不要在框架中运行Commerce店面。

## 实施 `X-Frame-Options`

设置值 `X-Frame-Options` 在 `<project-root>/app/etc/env.php`. 缺省值设置如下：

```php
'x-frame-options' => 'SAMEORIGIN',
```

重新部署对所做的任何更改 `env.php` 文件生效。

>[!TIP]
>
>这样可以更安全地编辑 `env.php` 文件，以在“管理员”中设置值。

## 验证您的设置 `X-Frame-Options`

要验证您的设置，请查看任何店面页面上的HTTP标头。 可通过多种方法做到这一点，包括使用Web浏览器检查器。

以下示例使用curl，您可以从任何可以通过HTTP协议连接到Commerce服务器的计算机运行它。

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

查找 `X-Frame-Options` 值。
