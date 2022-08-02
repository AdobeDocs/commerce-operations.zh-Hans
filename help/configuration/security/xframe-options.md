---
title: X-Frame-Options标题
description: 使用X-Frame-Options控制页面渲染。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# X-Frame-Options标题

帮助防止 [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) 利用漏洞，我们添加了一个选项 [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) 对您的店面的请求中的HTTP请求标头。

的 `X-Frame-Options` 标题允许您指定是否允许浏览器在 `<frame>`, `<iframe>`或 `<object>` 如下所示：

- `DENY`:页面无法在框架中显示。
- `SAMEORIGIN`:（默认）页面只能显示在与页面本身位于同一原点的框架中。

>[!WARNING]
>
>的 `ALLOW-FROM <uri>` 选项已被弃用，因为商务支持的浏览器不再支持它。 请参阅 [浏览器兼容性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>出于安全考虑，Adobe强烈建议不要在框架中运行Commerce商店店面。

## 实施 `X-Frame-Options`

为 `X-Frame-Options` in `<magento_root>/app/etc/env.php`. 默认值如下：

```php
'x-frame-options' => 'SAMEORIGIN',
```

>[!TIP]
>
>编辑 `env.php` 文件，而不是在管理员中设置值。

## 验证的设置 `X-Frame-Options`

要验证您的设置，请查看任何店面页面上的HTTP标头。 可通过多种方法来实现此目的，包括使用Web浏览器检查器。

以下示例使用curl，您可以从任何可以通过HTTP协议连接到商务服务器的计算机中运行curl。

使用以下命令：

```bash
curl -I -v --location-trusted '<your storefront URL>'
```

查找 `X-Frame-Options` 值。
