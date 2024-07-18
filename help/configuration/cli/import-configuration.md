---
title: 从配置文件导入数据
description: 从配置文件导入Adobe Commerce配置设置。
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# 导入配置设置

{{file-system-owner}}

使用Commerce 2.2 [管道部署模型](../deployment/technical-details.md)设置生产系统时，必须&#x200B;_将`config.php`和`env.php`中的_配置设置导入数据库。
这些设置包括配置路径和值、网站、商店、商店视图和主题。

导入网站、商店、商店视图和主题后，您可以创建产品属性，并在生产系统上将其应用于网站、商店和商店视图。

>[!INFO]
>
>`bin/magento app:config:import`命令不处理存储在环境变量中的配置。

## 导入命令

在生产系统上，运行以下命令以将数据从配置文件（`config.php`和`env.php`）导入数据库：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

使用可选的`[-n, --no-interaction]`标记导入数据，无需进行任何交互。

如果您输入的`bin/magento app:config:import`没有可选标记，则需要确认更改。

例如，如果配置文件包含一个新网站和一个新商店，则会显示以下消息：

```
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

要继续导入，请输入`yes`。

如果部署配置文件包含要导入的一些数据，则会显示一条与以下内容类似的消息：

```
Start import:
Some information about importing
```

如果部署配置文件不包含任何要导入的数据，则会显示一条与以下内容类似的消息：

```
Start import:
Nothing to import
```

## 我们导入的内容

以下部分详细讨论我们导入的数据。

### 系统配置

Commerce在`config.php`或`env.php`文件中直接使用`system`数组中的值，而不是将这些值导入数据库，因为它们需要一些预处理操作和后期处理操作。

例如，必须使用后端模型验证配置路径`web/secure/base_url`的值。

#### 后端模型

后端模型是处理系统配置更改的机制。
您在`<module_name>/adminhtml/system.xml`中定义后端模块。

所有后端模型都必须扩展[`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php)类。

导入后端模型时，不会保存配置值。

### 网站、商店和商店组配置

我们导入以下类型的配置。
（这些配置位于`config.php`中的`scopes`阵列下。）

- `websites`：网站相关配置
- `groups`：存储相关配置
- `stores`：存储视图相关配置

上述配置可在以下模式下导入：

- `create`： `config.php`包含生产环境中不存在的新实体(`websites`、`groups`、`stores`)
- `update`： `config.php`包含与生产环境不同的实体(`websites`、`groups`、`stores`)
- `delete`： `config.php` _不_&#x200B;包含生产环境中存在的实体(`websites`、`groups`、`stores`)

>[!INFO]
>
>我们不导入与存储关联的根类别。 您必须使用Commerce管理员将根类别与存储关联。

### 主题配置

主题配置包括在Commerce系统中注册的所有主题；数据直接来自`theme`数据库表。 （主题配置位于`config.php`中的`themes`数组中。）

#### 主题数据的结构

数组的键为完整主题路径： `area` + `theme path`

例如，`frontend/Magento/luma`。
`frontend`是区域，`Magento/luma`是主题路径。

数组的值是有关主题的数据：代码、标题、路径、父ID

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
>- _主题注册_。 如果在`config.php`中定义了主题数据，但文件系统中不存在该主题的源代码，则会忽略该主题（即，未注册）。
>- _主题移除_。 如果`config.php`中不存在主题，但文件系统中存在源代码，则不会移除主题。
