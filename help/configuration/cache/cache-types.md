---
title: 缓存类型
description: 将缓存前端与缓存类型关联。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 缓存类型

以下步骤将完成将缓存前端与缓存类型关联。

## 步骤1:定义缓存前端

商务应用程序具有 `default` 可用于任何 [缓存类型](../cli/manage-cache.md#clean-and-flush-cache-types). 本节将讨论如何选择定义使用不同名称的缓存前端，如果您希望自定义前端，最好使用此名称。

>[!INFO]
>
>使用 `default` 缓存类型，您无需修改 `env.php` 根本上；修改商务的全局 `di.xml`. 请参阅 [低级缓存选项](cache-options.md).

必须指定自定义缓存前端 `app/etc/env.php` 或商业的全球 `app/etc/di.xml`.

以下示例显示如何在 `env.php` 文件，该文件将覆盖 `di.xml` 文件：

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

其中 `<unique frontend id>` 是用于标识前端和 `<cache options>` 是特定于每种类型缓存（数据库、Redis等）的主题中讨论的选项。

## 步骤2:配置缓存

您可以在 `env.php` 或 `di.xml`. 此任务是可选的。

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

where

- `<frontend_type>` 是低级前端缓存类型。 指定与兼容的类的名称 [Zend\Cache\Core](https://framework.zend.com/apidoc/1.7/Zend_Cache/Zend_Cache_Core.html).

   如果忽略 `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 中，将使用。

- `<frontend_option>`, `<frontend_option_value>` 是商务框架在创建时将作为关联数组传递到前端缓存的选项的名称和值。
- `<backend_type>` 是低级后端缓存类型。 指定与兼容的类的名称 [Zend_Cache_Backend](https://framework.zend.com/apidoc/1.7/Zend_Cache/Zend_Cache_Backend/Zend_Cache_Backend.html) 和工具 [Zend_Cache_Backend_Interface](https://framework.zend.com/apidoc/1.6/Zend_Cache/Zend_Cache_Backend/Zend_Cache_Backend_Interface.html).
- `<backend_option>` 和 `<backend_option_value>` 是商务框架在创建时将作为关联数组传递到后端缓存的选项的名称和值。
