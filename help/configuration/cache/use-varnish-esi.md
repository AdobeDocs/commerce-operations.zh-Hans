---
title: 清漆ESI區塊
description: 瞭解Edge Side Include以及如何使用它們來內嵌網頁。
badge: label="Contributed by Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# 清漆ESI區塊

Edge Side Include (ESI)是特殊指令，可用來將網頁包含在其他網頁中。

範例：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

清漆從擷取內容 `http://domain.com/index.php/page_cache/block/esi/blocks` 並取代 `<esi>` 標籤此專案。

## Commerce與Varnish ESI

Commerce架構會在符合下列條件時建立ESI標籤：

- 快取應用程式設定為 `Varnish Cache`
- XML配置 `block` 元素新增了 `ttl` 屬性

### 範例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

在上述範例中， `block` 元素新增以下專案的內容： `esi.phtml` 範本至首頁，Varnish每30秒會自動更新一次。

## 限制

目前Varnish不支援HTTPS上的ESI，所以會自動切換至HTTP。

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
