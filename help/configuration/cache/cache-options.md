---
title: 缓存后端选项和存储参考
description: 了解Adobe Commerce中的缓存后端选项，包括文件系统、Redis、Valkey和数据库存储。 探索传统和现代方法。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 309
ht-degree: 0%

---

# 缓存后端选项和存储参考

{{cloud-cache-config}}

Commerce应用程序使用低级缓存前端和后端来提供对缓存存储的访问。 Commerce支持多种缓存后端和策略，每种后端和策略都适用于不同的用例。 本页介绍可用的后端及其差异。

## 后端缓存选项

下表汇总了可用的后端缓存：

| 后端 | 描述 | 配置指南 |
| ------- | ----------- | ------------------- |
| 文件系统 | 默认。 将缓存数据存储在`var/cache/`下的文件中。 无需配置。 | 不适用 |
| [红色](config-redis.md) | 用于高性能缓存的内存中数据存储。 | [对默认缓存使用Redis](redis-pg-cache.md) |
| [Valkey](config-valkey.md) | 开源、与Redis兼容的替代方案。 | [对默认缓存使用Valkey](valkey-pg-cache.md) |
| [数据库](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | 数据库支持的缓存。 | [创建自定义缓存引擎](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} （Adobe开发人员文档） |

>[!NOTE]
>
>[Varnish](config-varnish.md)在HTTP级别处理全页缓存，不使用低级缓存后端。

## 实施方法

Commerce支持两种后端实施方法。 您选择的方法取决于您的Commerce版本：

>[!BEGINTABS]

>[!TAB 基于Zend的旧版缓存（2.4.8及更早版本）]

对后端配置使用完整类名：

| 后端 | 类名称 |
| ------- | ---------- |
| Redis | `Magento\Framework\Cache\Backend\Redis` |
| Valkey | `Magento\Framework\Cache\Backend\Valkey` |

这些与`Zend_Cache_Backend`接口兼容。

**示例配置：**

```php?start_inline=1
'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
],
```

>[!TAB 现代Symfony缓存（建议使用2.4.9及更高版本）]

>[!TIP]
>
>现代Symfony缓存实现通过PSR-6合规性、Igbinary序列化、gzip压缩、Lua脚本和永久连接提供了更好的性能。

使用简化的后端类型名称：

| 后端 | 键入名称 |
| ------- | --------- |
| Redis | `redis` |
| Valkey | `valkey` |
| 文件系统 | `file` |

**示例配置：**

```php?start_inline=1
'backend' => 'redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
    'serializer' => 'igbinary',
    'compression_lib' => 'gzip',
],
```

>[!ENDTABS]

有关完整的配置选项，请参阅：

- [将Redis用于默认缓存](redis-pg-cache.md)
- [将Valkey用于默认缓存](valkey-pg-cache.md)
- [二级缓存配置](level-two-cache.md)

有关基于Zend的旧版选项，请参阅[Laminas文档](https://docs.laminas.dev/)。
