---
title: 清漆ESI块
description: 了解Edge Side Include以及如何使用它们嵌入网页。
badge: label="Contributed by Konstantin G." type="Informational" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# 清漆ESI块

Edge Side Include (ESI)是特殊指令，可用于将网页包含在其他网页中。

示例：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

清漆从以下位置提取内容 `http://domain.com/index.php/page_cache/block/esi/blocks` 并替换 `<esi>` 标记它。

## Commerce和Varnish ESI

Commerce框架会在满足以下条件时创建ESI标记：

- 缓存应用程序设置为 `Varnish Cache`
- XML布局 `block` 元素添加了 `ttl` 属性

### 示例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

在上例中， `block` 元素添加来自以下项的内容： `esi.phtml` 模板到主页，Varnish每30秒自动更新一次。

## 限制

目前，Varnish不支持HTTPS上的ESI，因此它会自动切换到HTTP。

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
