---
title: 导出配置设置
description: 将Adobe Commerce配置设置导出到配置文件，也称为配置转储。
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# 导出配置设置

在Commerce 2.2及更高版本中 [管道部署模型](../deployment/technical-details.md)，您可以跨系统维护一致的配置。 在开发系统的“管理员”中配置设置后，使用以下命令将这些设置导出到配置文件：

```bash
bin/magento app:config:dump {config-types}
```

_config_type_ 是要转储的配置类型列表（以空格分隔）。 可用的类型包括 `scopes`， `system`， `themes`、和 `i18n`. 如果未指定配置类型，则命令将转储所有系统配置信息。

以下示例仅转储范围和主题：

```bash
bin/magento app:config:dump scopes themes
```

命令执行后，将更新以下配置文件：

- `app/etc/config.php`

  这是所有Commerce实例的共享配置文件。
将此包括在源代码管理中，以便在开发、构建和生产系统之间共享。

  请参阅 [config.php引用](../reference/config-reference-configphp.md).

- `app/etc/env.php`

  这是特定于环境的配置文件。
它包含适用于各个环境的敏感和特定于系统的设置。

  Do _非_ 将此文件包含在源代码管理中。

  请参阅 [env.php参考](../reference/config-reference-envphp.md).

## 敏感或系统特定的设置

设置写入到的敏感设置 `env.php`，使用 [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) 命令。

通过引用将配置值指定为敏感值或系统特定值 [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) 在模块的 [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) 文件。

使用时导出其他系统设置 `config_types`，考虑使用 [`bin/magento config:set`](set-configuration-values.md#set-values) 命令。
