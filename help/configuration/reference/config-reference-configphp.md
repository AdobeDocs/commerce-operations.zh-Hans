---
title: config.php引用
description: 请参阅config.php文件中的值列表。
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# config.php引用

的 `config.php` 文件包含以下部分：

| 名称 | 描述 |
| --------- | -------------------|
| `i18n` | 所有内联翻译数据。 不支持从此部分读取。 |
| `modules` | 已启用和已禁用模块的列表。 |
| `scopes` | 包含相关信息的商店、商店组和网站的列表。 |
| `system` | 静态内容部署所需的系统配置。 |
| `themes` | 已安装主题的配置。 |

## 模块

包含一组模块及其状态。 如果已启用模块，则值为1。 否则，值为0。

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

详细了解 [模块].

## 范围

包含作用域配置值数组。 它具有以下子节点：

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

详细了解 [商务范围][scopes].

## 系统

包含系统字段配置值数组。

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

详细了解 [特定于系统的配置](config-reference-sens.md).

## 主题

包含主题配置的值数组。

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

详细了解 [主题].

<!-- link definitions -->

[模块]: https://devdocs.magento.com/videos/fundamentals/create-a-new-module/
[scopes]: https://docs.magento.com/user-guide/configuration/scope.html
[主题]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/theme-create.html