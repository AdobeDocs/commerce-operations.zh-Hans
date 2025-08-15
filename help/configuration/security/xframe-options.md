---
title: 防止点击劫持攻击
description: 通过使用“X-Frame-Options”标头控制页面渲染来阻止点击劫持攻击。
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 防止点击劫持攻击

通过在店面的请求中包含[X-Frame-Options](https://owasp.org/www-community/attacks/Clickjacking) HTTP请求标头，防止[点击劫持](https://datatracker.ietf.org/doc/html/rfc7034)攻击。

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

在`X-Frame-Options`中设置`<project-root>/app/etc/env.php`的值。 缺省值设置如下：

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

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

在标头中查找`X-Frame-Options`值。
