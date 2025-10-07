---
title: config.php引用
description: 了解Adobe Commerce配置的config.php文件值和部分。 发现模块、范围、系统设置和部署最佳实践。
exl-id: 9b355d6d-ea66-480b-ad96-0ea9e7e61844
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 1%

---

# config.php引用

`config.php`文件包含以下部分：

| 名称 | 描述 |
| --------- | -------------------|
| `i18n` | 所有内联翻译数据。 不支持读取此部分。 |
| `modules` | 已启用和已禁用的模块列表。 |
| `scopes` | 包含相关信息的商店、商店组和网站的列表。 |
| `system` | 静态内容部署所需的系统配置。 |
| `themes` | 已安装主题的配置。 |

## 模块

包含一系列模块及其状态。 如果启用了模块，则值为1。 否则，值为0。

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

了解有关[模块]的详细信息。

## 范围

包含作用域配置值的数组。 它包含以下子节点：

| 名称 | 描述 |
| ---------- | -----------------------------------|
| `websites` | 网站配置 |
| `groups` | 存储配置 |
| `stores` | 存储视图配置 |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

了解有关[Commerce作用域][scopes]的更多信息。

## 系统

包含系统字段配置值的数组。

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

了解有关[特定于系统的配置](config-reference-sens.md)的详细信息。

## 主题

包含主题配置的值的数组。

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

了解有关[主题]的更多信息。

<!-- link definitions -->

[模块]: https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html
[scopes]: https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings
[主题]: https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/
