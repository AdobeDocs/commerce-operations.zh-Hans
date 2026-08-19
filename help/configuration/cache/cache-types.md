---
title: 配置缓存前端和类型
description: 了解如何在Adobe Commerce中定义缓存前端并将它们与缓存类型相关联。 探索env.php的配置语法。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2: id: cdf0c6dd-1717-4e20-9530-a24eee57088bid: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 3652976a8db3d0bb19ff9cd06adb3a7736c89539
workflow-type: tm+mt
source-wordcount: 398
ht-degree: 0%

---

# 配置缓存前端和类型

缓存前端将Commerce缓存类型连接到缓存存储。 您可以定义多个前端，并为每个前端分配特定的缓存类型。

>[!BEGINSHADEBOX]

使用以下关系来确定缓存类型存储其数据的位置：

缓存类型→缓存前端→缓存后端

>[!ENDSHADEBOX]

有关Commerce缓存体系结构的概述，请参阅[缓存概述和配置选项](caching-overview.md)。

>[!NOTE]
>
>对于云基础架构上的Adobe Commerce，请使用云指南中描述的[云部署配置](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/configure-env-yaml)。 不要直接编辑`app/etc/env.php`。 部署工具会生成此文件并会覆盖手动更改。

## 使用默认前端

Commerce提供了一个可供所有缓存类型使用的默认前端。

在大多数情况下，您无需定义自定义前端。 如果所有缓存类型都可以使用相同的后端和后端选项，请使用默认前端并配置其后端。 有关特定于后端的配置，请参阅[缓存后端选项](cache-options.md)。

对于2.4.9之前的Adobe Commerce版本，默认前端使用旧版基于Zend的缓存实施。 `Magento\Framework\Cache\Core`前端扩展`Zend_Cache_Core`。 Adobe Commerce 2.4.9及更高版本使用现代化的Symfony实施。 有关特定于版本的指导，请参阅[缓存后端选项](cache-options.md)。

## 定义自定义前端

当一个或多个缓存类型需要与默认前端不同的后端设置时，请使用自定义缓存前端。

对于内部部署，请在`app/etc/env.php`中定义前端。 然后为其分配一个或多个缓存类型：

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<frontend-id>' => [
            'backend' => '<backend-type>',
            'backend_options' => [
                // Backend-specific options
            ],
        ],
    ],
    'type' => [
        '<cache-type-id>' => [
            'frontend' => '<frontend-id>',
        ],
    ],
],
```

其中：

- `<frontend-id>`是前端的唯一标识符，如`default`或`page_cache`。
- `<backend-type>`标识前端使用的后端。 支持的值取决于Adobe Commerce版本和选定的后端。
- `backend_options`包含选定后端的选项。
- `<cache-type-id>`是Commerce缓存类型，如`config`、`layout`、`block_html`或`full_page`。


有关后端类型、支持的选项和特定于发行版的配置示例，请参阅[缓存后端选项](cache-options.md)。

## 将缓存类型分配给前端

`type`配置将缓存类型映射到前端：

```php?start_inline=1
'type' => [
    'full_page' => [
        'frontend' => 'page_cache',
    ],
],
```

在此示例中，Commerce将`full_page`缓存类型分配给`page_cache`前端。 前端确定存储该缓存类型的后端配置。

>[!NOTE]
>
>`full_page`键表示Commerce应用程序缓存类型。 通过Varnish或Fastly的HTTP全页缓存是一个单独的缓存层。 请参阅[缓存概述和配置选项](caching-overview.md)。

>[!MORELIKETHIS]
>
>- 用于性能优化的[二级缓存配置](level-two-cache.md)
>- [管理缓存](../cli/manage-cache.md)
