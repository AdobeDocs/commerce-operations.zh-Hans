---
title: 配置清漆ESI块
description: 了解Varnish Edge Side Include (ESI)以及如何嵌入Adobe Commerce的网页。 发现ESI块的实施和优化。
badge: label="由Konstantin G提供。" type="Informative" url="https://github.com/goivvy" tooltip="康斯坦丁G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hans/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
autotag-review: '2026-06-22T22:02:08.706Z'
TQID: 'https://experienceleague.adobe.com/hzsfaZyHuUhzfb86anO43PfP-62WRPOoMbYOh-H1vqo'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 159
ht-degree: 0%

---

# 配置清漆ESI块 {#varnish-esi-block}

{{varnish-config-cloud}}

Edge Side Include (ESI)是特殊指令，可用于将网页包含在其他网页中。

示例：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

清漆从`http://domain.com/index.php/page_cache/block/esi/blocks`中获取内容，并用它替换`<esi>`标记。

## Commerce和清漆ESI

Commerce框架会在满足以下条件时创建ESI标记：

- 缓存应用程序设置为`Varnish Cache`
- 已添加具有`ttl`特性的XML布局`block`元素

### 示例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

在上述示例中，`block`元素将来自`esi.phtml`模板的内容添加到主页，Varnish每30秒自动更新一次。

## 限制

目前，Varnish不支持通过HTTPS进行ESI，因此会自动切换到HTTP。

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
