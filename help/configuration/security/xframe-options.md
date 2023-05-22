---
title: X-Frame-Options標頭
description: 使用X-Frame-Options來控制頁面轉譯。
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# X-Frame-Options標頭

協助防止 [點選劫持](https://owasp.org/www-community/attacks/Clickjacking) 利用漏洞，我們新增了一個選項來使用 [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) 對店面的請求中的HTTP請求標頭。

此 `X-Frame-Options` 頁首可讓您指定是否允許瀏覽器在中轉譯頁面 `<frame>`， `<iframe>`，或 `<object>` 如下所示：

- `DENY`：頁面無法顯示在框架中。
- `SAMEORIGIN`：（預設）頁面只能在與頁面本身相同原始位置的框架中顯示。

>[!WARNING]
>
>此 `ALLOW-FROM <uri>` 選項已過時，因為Commerce支援的瀏覽器不再支援該選項。 另請參閱 [瀏覽器相容性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>基於安全考量，Adobe強烈建議不要在框架中執行Commerce店面。

## 實作 `X-Frame-Options`

設定值 `X-Frame-Options` 在 `<project-root>/app/etc/env.php`. 預設值設定如下：

```php
'x-frame-options' => 'SAMEORIGIN',
```

針對任何變更重新部署 `env.php` 檔案生效。

>[!TIP]
>
>編輯會更安全 `env.php` 在「管理員」中設定值。

## 驗證您的設定 `X-Frame-Options`

若要驗證您的設定，請檢視任何店面頁面上的HTTP標題。 有數種方法可以達成此目的，包括使用網頁瀏覽器檢測器。

以下範例使用curl，您可以從任何可透過HTTP通訊協定連線至您的Commerce伺服器的電腦執行它。

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

尋找 `X-Frame-Options` 值標頭中的。
