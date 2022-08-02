---
title: 导出配置设置
description: 将Adobe Commerce配置设置导出到配置文件，也称为配置转储。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# 导出配置设置

在Commerce 2.2及更高版本中 [管道部署模型](../deployment/technical-details.md)，则可以跨系统保持一致的配置。 在开发系统的“管理员”中配置设置后，使用以下命令将这些设置导出到配置文件：

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ 是要转储的配置类型列表（以空格分隔）。 可用类型包括 `scopes`, `system`, `themes`和 `i18n`. 如果未指定配置类型，则命令会转储所有系统配置信息。

以下示例仅转储范围和主题：

```bash
bin/magento app:config:dump scopes themes
```

执行命令后，将更新以下配置文件：

- `app/etc/config.php`

   这是所有Commerce实例的共享配置文件。
将此内容包含在源代码管理中，以便在开发、构建和生产系统之间共享。

   请参阅 [config.php引用](../reference/config-reference-configphp.md).

- `app/etc/env.php`

   这是特定于环境的配置文件。
它包含适用于各个环境的特定于系统的敏感设置。

   做 _not_ 将此文件包含在源代码管理中。

   请参阅 [env.php引用](../reference/config-reference-envphp.md).

## 敏感或系统特定的设置

设置写入的敏感设置 `env.php`，则使用 [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) 命令。

通过引用，可将配置值指定为敏感值或特定于系统的值 [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) 的 [`di.xml`](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/configuration/sensitive-and-environment-settings.html#how-to-specify-values-as-sensitive-or-system-specific) 文件。

在使用 `config_types`，请考虑使用 [`bin/magento config:set`](set-configuration-values.md#set-values) 命令。
