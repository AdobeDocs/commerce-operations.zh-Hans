---
title: 部署的配置文件
description: 了解配置文件如何用于安装商务应用程序。
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: dd990800551dd2ba35ebc7d2bc04edeb1b183d6f
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 部署的配置文件

Adobe Commerce提供了配置文件，使您能够轻松自定义组件并创建配置类型以扩展默认功能。 部署配置过程包括安装的共享配置和特定于系统的配置。 商务的部署配置分为 [`app/etc/config.php`](../reference/config-reference-configphp.md) 和 [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` 是 _共享_ 配置文件。
该文件包含已安装的模块、主题和语言包的列表；和共享配置设置。

   将此文件签入到源代码管理中，并将其用在您的开发、暂存和生产系统中。

- `app/etc/env.php` 包含特定于安装环境的设置。

一起， `config.php` 和 `env.php` 称为“商务” _部署配置_ 因为文件是在安装期间创建的，并且需要启动商务应用程序。

>[!INFO]
>
>的 [!DNL Commerce 2] 部署配置替换 `local.xml` in [!DNL Magento 1.x].

与其他 [模块配置文件](../reference/module-files.md)，则在初始化期间，Commerce部署配置将加载到内存中，未与任何其他文件合并，且无法扩展。 (`config.php` 和 `env.php` 但是会相互合并。)

## 有关部署配置的详细信息

`config.php` 和 `env.php` 是返回 [多维关联阵列](https://www.w3schools.com:443/php/php_arrays.asp)，这基本上是配置参数和值的层次结构。

此数组的顶级为 _配置区段_. 区段具有由任意键区分的任意内容（标量值或嵌套数组），其中键和值对都由商务框架定义。

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) 仅提供对这些部分的访问权限，但不允许您扩展这些部分。

在下一层级上，每个区段中的项目根据模块顺序定义进行排序，该定义通过合并所有模块的配置文件来获取，但禁用模块除外。

以下各节将讨论部署配置的结构和内容：

- 管理已安装的模块
- 特定于系统的配置

## 管理已安装的模块

的 `config.php` 文件包含已安装模块的列表。 Adobe Commerce提供了命令行和基于web的实用程序来管理模块（安装、卸载、启用、禁用或升级）。

示例：

- 卸载组件： [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- 检查组件状态： [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- 启用或禁用组件： [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

值 `1` 或 `0` 指示模块是已启用还是已禁用。

Commerce应用程序无法识别禁用的模块；换言之，他们不会参与合并配置、依赖关系注入、事件、插件等。 禁用的模块不会修改店面或管理员，也不会影响路由。

在代码库中，禁用模块和缺失模块的唯一实际区别在于，自动加载器找到了禁用模块，其类和常量可在其他代码中重复使用。
