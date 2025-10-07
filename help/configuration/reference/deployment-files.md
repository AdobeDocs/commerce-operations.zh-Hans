---
title: 用于部署的配置文件
description: 了解配置文件如何用于Adobe Commerce应用程序部署。 了解共享和特定于系统的配置管理最佳实践。
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# 用于部署的配置文件

Adobe Commerce提供了配置文件，使您能够轻松自定义组件和创建配置类型以扩展默认功能。 部署配置过程包含用于安装的共享配置和特定于系统的配置。 Commerce的部署配置在[`app/etc/config.php`](../reference/config-reference-configphp.md)和[`app/etc/env.php`](../reference/config-reference-envphp.md)之间分配。

- `app/etc/config.php`是&#x200B;_共享_配置文件。
此文件包含已安装的模块、主题和语言包的列表；以及共享的配置设置。

  将此文件签入到源代码管理，并将其用于开发、暂存和生产系统。

- `app/etc/env.php`包含特定于安装环境的设置。

`config.php`和`env.php`一起称为Commerce _部署配置_，因为这两个文件是在安装期间创建的，并且是启动Commerce应用程序所必需的。

>[!INFO]
>
>[!DNL Commerce 2]部署配置替换了`local.xml`中的[!DNL Magento 1.x]。

与其他[模块配置文件](../reference/module-files.md)不同，Commerce部署配置在初始化期间加载到内存中，不会与任何其他文件合并，并且无法扩展。 （`config.php`和`env.php`已相互合并。）

## 有关部署配置的详细信息

`config.php`和`env.php`是返回[多维关联数组](https://www.w3schools.com:443/php/php_arrays.asp)的PHP文件，该数组基本上是配置参数和值的分层排列。

此数组的顶层是&#x200B;_配置区段_。 区段具有由任意键区分的任意内容（标量值或嵌套数组），其中键和值对均由Commerce Framework定义。

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php)仅提供对这些部分的访问权限，不允许您扩展它们。

在下一个层次上，每个模块中的项目按照模块顺序定义排序，该顺序是通过合并所有模块的配置文件得到的，禁用模块除外。

以下部分讨论了部署配置的结构和内容：

- 管理已安装的模块
- 系统特定的配置

## 管理已安装的模块

`config.php`文件包含已安装模块的列表。 Adobe Commerce提供命令行和基于Web的实用程序来管理模块（安装、卸载、启用、禁用或升级）。

示例：

- 卸载组件： [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- 检查组件的状态： [`bin/magento module:status`](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/cli-reference/commerce-on-premises#modulestatus)
- 启用或禁用组件： [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md)，[`bin/magento module:enable`](../../installation/tutorials/manage-modules.md)。

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

值`1`或`0`指示模块是启用还是禁用。

Commerce应用程序无法识别禁用的模块；换言之，它们不参与合并配置、依赖项注入、事件、插件等。 禁用的模块不会修改店面或管理员，也不会影响路由。

代码库中禁用模块和缺失模块的唯一实际区别是，禁用模块由自动加载器找到，其类和常量可在其他代码中重用。
