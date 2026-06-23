---
title: 配置缓存前端
description: 了解如何在Adobe Commerce中定义缓存前端并将它们与缓存类型相关联。 发现env.php和di.xml的配置语法。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ae31702797c8754a719e5a5eb39a3924e723c87a
workflow-type: tm+mt
source-wordcount: 454
ht-degree: 0%

---

# 配置缓存前端

缓存前端是Commerce和缓存存储后端之间的接口。 您可以定义多个前端，每个前端具有不同的后端设置，然后为每个前端分配特定的[缓存类型](../cli/manage-cache.md#clean-and-flush-cache-types)。

当您希望对不同类型的缓存数据使用不同的缓存后端或配置时，这将很有用。 例如，您可能希望在专用Redis数据库上进行`full_page`缓存，同时为`default`缓存使用单独的数据库。

{{cloud-cache-config}}

## 使用默认前端

Commerce提供了一个适用于所有缓存类型的`default`缓存前端。 它通过实现[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)前端缓存来扩展[Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html)。

在大多数情况下，您无需自定义前端。 您只需要配置后端。 请参阅[缓存后端选项](cache-options.md)。

## 定义自定义缓存前端

以下步骤逐步说明如何将缓存前端与缓存类型相关联。

### 步骤1：定义缓存前端并分配缓存类型

要定义自定义缓存前端，请将配置添加到`app/etc/env.php`（覆盖`di.xml`）：

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

其中：

- `<unique frontend id>` — 用于标识前端的唯一名称（例如，`default`、`page_cache`、`stale_cache_enabled`）
- `<cache options>` — 此前端的后端类型和选项（请参阅[缓存选项](cache-options.md)）
- `<cache type>` — 要分配给此前端的Commerce缓存类型（例如，`config`、`layout`、`block_html`、`full_page`）

>[!TIP]
>
>**现代Symfony缓存实现(2.4.9+)：**&#x200B;从Commerce 2.4.9开始，您可以将`redis`、`valkey`或`file`等简化的后端类型用于现代Symfony缓存实现。 有关详细信息，请参阅[对默认缓存使用Redis](redis-pg-cache.md)和[对默认缓存使用Valkey](valkey-pg-cache.md)。

### 步骤2：配置前端和后端选项

您可以在`env.php`或`di.xml`中指定前端和后端缓存配置选项。 此任务是可选的。 如果不指定选项，Commerce将使用默认的前端和后端设置。

`env.php`示例：

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

其中：

- `<frontend_type>` — 低级前端缓存类型。指定与`Zend\Cache\Core`兼容的类名。
如果省略，则使用[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)。

- `<frontend_option>`， `<frontend_option_value>` — Commerce框架在创建时作为关联数组传递给前端缓存的选项的名称和值。

- `<backend_type>` — 低级后端缓存类型。 您可以指定：
   - **现代Symfony缓存（2.4.9+，推荐）**：简化名称，如`redis`、`valkey`或`file`
   - **旧版（基于Zend）**：与实现`Zend_Cache_Backend_Interface`的`Zend_Cache_Backend`兼容的完整类名

- `<backend_option>`， `<backend_option_value>` — Commerce框架在创建时作为关联数组传递给后端缓存的选项的名称和值。

>[!NOTE]
>
>**旧版与新版实施：**
>
>- **旧版（基于Zend）**： `'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis'`
>- **现代（Symfony缓存）**： `'backend' => 'redis'` （建议用于Commerce 2.4.9+）
>
>现代Symfony缓存实现通过PSR-6合规性、Igbinary序列化、gzip压缩、Lua脚本和永久连接提供了更好的性能。

有关基于Zend的选项，请参阅[Laminas文档](https://docs.laminas.dev/)。 有关Symfony缓存配置，请参阅本文档中的[Redis](redis-pg-cache.md)和[Valkey](valkey-pg-cache.md)文章。
