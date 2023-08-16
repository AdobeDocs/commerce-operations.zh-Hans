---
title: 缓存类型
description: 将缓存前端与缓存类型相关联。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# 缓存类型

以下步骤逐步说明如何将缓存前端与缓存类型相关联。

## 步骤1：定义缓存前端

商务应用程序具有 `default` 缓存前端，可用于任何 [缓存类型](../cli/manage-cache.md#clean-and-flush-cache-types). 此部分讨论如何选择性地使用不同的名称定义缓存前端，如果您希望自定义前端，最好使用不同的名称。

>[!INFO]
>
>要使用 `default` 缓存类型，您无需修改 `env.php` 您根本可以修改Commerce的全局 `di.xml`. 请参阅 [低级缓存选项](cache-options.md).

您必须指定自定义缓存前端 `app/etc/env.php` 或Commerce的全局 `app/etc/di.xml`.

以下示例说明如何在 `env.php` 文件，覆盖 `di.xml` 文件：

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
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

位置 `<unique frontend id>` 是用于标识前端和的唯一名称 `<cache options>` 这些是特定于每种缓存类型（数据库、Redis等）的主题中讨论的选项。

## 步骤2：配置缓存

您可以在中指定前端和后端缓存配置选项 `env.php` 或 `di.xml`. 此任务是可选的。

`env.php` 示例：

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

位置

- `<frontend_type>` 是低级前端缓存类型。 指定与兼容的类的名称 `Zend\Cache\Core`.
如果忽略 `<frontend_type>`， [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 已使用。

- `<frontend_option>`， `<frontend_option_value>` 是Commerce框架在创建时作为关联数组传递到前端缓存的选项的名称和值。
- `<backend_type>` 是低级后端缓存类型。 指定与兼容的类的名称 `Zend_Cache_Backend` 并且实现 `Zend_Cache_Backend_Interface`.
- `<backend_option>` 和 `<backend_option_value>` 是Commerce框架在创建后端缓存时作为关联数组传递的选项的名称和值。

请参阅 [Laminas文档](https://docs.laminas.dev/) 以获取最新的Zend信息。
