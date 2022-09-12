---
title: 数据迁移设置
description: 了解如何开始将设置从Magento1迁移到Magento2，使用 [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 数据迁移设置

的 `Settings` 模式迁移商店、网站和系统配置，如装运、付款和税务设置。 根据我们的数据迁移 [订购](overview.md#migration-order)，则应首先迁移设置。

在开始之前，请采取以下步骤进行准备：

1. 以 [文件系统所有者](../../../installation/prerequisites/file-system/overview.md).

1. 更改为 `/bin` 目录，或确保将其添加到系统中 `PATH`.

>[!NOTE]
>
>确保Magento2已部署在 `default` 模式。 开发人员模式可能会导致迁移工具中出现验证错误。


请参阅 [首要步骤](overview.md#first-steps) 部分以了解更多详细信息。

## 运行设置迁移命令

要开始迁移设置，请运行：

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]` 是从头开始迁移的可选参数。 您可以使用此参数测试迁移

* `[-a|--auto]` 是一个可选参数，可阻止迁移在遇到完整性检查错误时停止。

* `{<path to config.xml>}` 是迁移工具的绝对文件系统路径 [`config.xml`](../configure.md#configure-migration-in-vendor-folder) 文件；此参数是必需的。

>[!NOTE]
>
>此命令不会迁移所有配置设置。 验证Magento2中的所有设置 [管理员](https://glossary.magento.com/admin) 继续之前。


的 `Migration completed` 设置成功传输后，将显示消息。

## 配置自定义迁移规则

迁移设置时，您可以忽略、重命名或更改系统配置。 为此，请在 `settings.xml` 文件。

1. 作为或切换到的应用程序服务器登录 [文件系统所有者](../../../installation/prerequisites/file-system/overview.md).

1. 更改为以下目录：

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   例如，如果应用程序安装在 `/var/www/html`, `settings.xml.dist` 文件位于以下目录之一中：

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. 创建 `settings.xml` 文件，运行：

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. 在 `settings.xml`.

1. 要指定要映射的设置文件的新名称，请更改 `<settings_map_file>` 标记 `path/to/config.xml` 文件。

有关更多详细信息，请参阅 [设置迁移模式](../technical-specification.md#settings-migration-mode) 工具的 [规范](../technical-specification.md).

## 下一迁移步骤

* [迁移数据](data.md)
