---
title: 清漆ESI块
description: 了解边缘端包含以及如何使用它们嵌入网页。
contributor_name: Goivvy LLC
contributor_link: https://www.goivvy.com/magento-optimization-service
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# 清漆ESI块

边缘端包含(ESI)是一些特殊指令，可用于将网页包含在其他网页中。

示例：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

清漆从中提取内容 `http://domain.com/index.php/page_cache/block/esi/blocks` 并替换 `<esi>` 标记。

## 商务和清漆ESI

当满足以下条件时，商务框架会创建一个ESI标记：

- 缓存应用程序设置为 `Varnish Cache`
- XML布局 `block` 元素添加了 `ttl` 属性

### 示例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

在上例中， `block` 元素会从 `esi.phtml` 主页模板和清漆会每30秒自动更新一次。

## 限制

目前，Quist不支持通过HTTPS的ESI，因此它会自动切换到HTTP。

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
