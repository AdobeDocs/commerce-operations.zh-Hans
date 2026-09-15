---
title: 配置缓存前端和类型
description: 了解如何在Adobe Commerce中定义缓存前端并将它们与缓存类型相关联。 探索env.php的配置语法。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '471'
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

其中：

- `<frontend_type>` — 低级前端缓存类型。 指定与`Zend_Cache_Core`兼容的类名。
如果省略，则使用[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)。

- `<frontend_option>`， `<frontend_option_value>` — Commerce框架在创建时作为关联数组传递给前端缓存的选项的名称和值。

- `<backend_type>` — 低级后端缓存类型。 您可以指定：
  - **Symfony缓存（2.4.9+，推荐）**：简化的名称，如`valkey`或`file`
  - 基于&#x200B;**Zend**：与实现`Zend_Cache_Backend_Interface`的`Zend_Cache_Backend`兼容的完整类名

- `<backend_option>`， `<backend_option_value>` — Commerce框架在创建时作为关联数组传递给后端缓存的选项的名称和值。

>[!NOTE]
>
>对于后端值格式，如基于Zend的类名与Symfony缓存的简化名称，如`valkey`或`file`，请参阅[缓存后端选项](cache-options.md)。

>[!MORELIKETHIS]
>
>- 用于性能优化的[二级缓存配置](level-two-cache.md)
>- [管理缓存](../cli/manage-cache.md)
