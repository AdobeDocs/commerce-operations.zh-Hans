---
title: 从配置文件导入数据
description: 从配置文件导入Adobe Commerce配置设置。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# 导入配置设置

{{file-system-owner}}

使用Commerce 2.2设置生产系统时 [管道部署模型](../deployment/technical-details.md)，您必须 _导入_ 配置设置 `config.php` 和 `env.php` 进入数据库。
这些设置包括配置路径和值、网站、存储、存储视图和主题。

在导入网站、存储、存储视图和主题后，您可以创建产品属性，并将其应用到生产系统上的网站、存储和存储视图。

>[!INFO]
>
>的 `bin/magento app:config:import` 命令不处理存储在环境变量中的配置。

## 导入命令

在生产系统上，运行以下命令以从配置文件导入数据(`config.php` 和 `env.php`)到数据库：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

使用可选 `[-n, --no-interaction]` 标记以导入数据，而无需进行任何交互。

如果输入 `bin/magento app:config:import` 如果没有可选标记，则需要确认更改。

例如，如果配置文件包含一个新网站和一个新商店，则会显示以下消息：

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

要继续导入，请输入 `yes`.

如果部署配置文件包含要导入的某些数据，则会显示与以下内容类似的消息：

```terminal
Start import:
Some information about importing
```

如果部署配置文件不包含任何要导入的数据，则会显示类似以下消息：

```terminal
Start import:
Nothing to import
```

## 我们导入的内容

以下各节详细讨论了我们导入的数据。

### 系统配置

商务直接使用 `system` 数组 `config.php` 或 `env.php` 文件，而不是将它们导入数据库，因为它们需要一些预处理和后处理操作。

例如，配置路径的值 `web/secure/base_url` 必须使用后端模型进行验证。

#### 后端模型

后端模型是处理系统配置更改的机制。
您可以在 `<module_name>/adminhtml/system.xml`.

所有后端模型必须 [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) 类。

导入后端模型时，不会保存配置值。

### 网站、商店和商店组配置

我们会导入以下类型的配置。
(这些配置位于 `scopes` 阵列 `config.php`.)

- `websites`:网站相关配置
- `groups`:存储相关配置
- `stores`:存储视图相关配置

以下模式可导入上述配置：

- `create`: `config.php` 包含新实体(`websites`, `groups`, `stores`)
- `update`: `config.php` 包含实体(`websites`, `groups`, `stores`)与生产环境不同
- `delete`: `config.php` does _not_ 包含实体(`websites`, `groups`, `stores`)

>[!INFO]
>
>我们不导入与存储关联的根类别。 您必须使用商务管理员将根类别与商店关联。

### 主题配置

主题配置包括在您的商务系统中注册的所有主题；数据直接来自 `theme` 数据库表。 (主题配置位于 `themes` 阵列 `config.php`.)

#### 主题数据的结构

数组的键是完整主题路径： `area` + `theme path`

例如， `frontend/Magento/luma`.
`frontend` 为面积和 `Magento/luma` 是主题路径。

数组的值是有关主题的数据：代码，标题，路径，父id

完整示例：

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _主题注册_. 如果在 `config.php` 但是该主题的源代码在文件系统中不存在，该主题将被忽略（即，未注册）。
>- _主题移除_. 如果主题不存在 `config.php` 但是，源代码存在于文件系统中，不会删除主题。

