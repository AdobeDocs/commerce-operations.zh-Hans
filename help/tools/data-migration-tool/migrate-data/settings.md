---
title: 数据迁移设置
description: 了解如何使用，开始将设置从Magento1迁移到Magento2 [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# 数据迁移设置

此 `Settings` 模式可迁移商店、网站和系统配置，如运费、付款和税务设置。 根据我们的数据迁移 [订购](overview.md#migration-order)，您应该先迁移设置。

在开始之前，请执行以下步骤进行准备：

1. 以以下身份登录到应用程序服务器 [文件系统所有者](../../../installation/prerequisites/file-system/overview.md).

1. 更改为 `/bin` 目录，或确保将其添加到您的系统中 `PATH`.

>[!NOTE]
>
>确保在中部署Magento2 `default` 模式。 开发人员模式可能会导致迁移工具中出现验证错误。


请参阅 [首要步骤](overview.md#first-steps) 部分以了解更多详细信息。

## 运行设置迁移命令

要开始迁移设置，请运行：

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]` 是一个可选参数，可从头开始迁移。 可以使用此参数测试迁移

* `[-a|--auto]` 是一个可选参数，可在遇到完整性检查错误时阻止停止迁移。

* `{<path to config.xml>}` 是迁移工具的绝对文件系统路径 [`config.xml`](../configure.md#configure-migration-in-vendor-folder) 文件；此参数是必需的。

>[!NOTE]
>
>此命令不会迁移所有配置设置。 在继续操作之前，请验证“Magento2管理”中的所有设置。


此 `Migration completed` 成功传输设置后将显示消息。

## 配置自定义迁移规则

迁移设置时，可以忽略、重命名或更改系统配置。 为此，请在 `settings.xml` 文件。

1. 以或切换至以下身份登录到应用程序服务器： [文件系统所有者](../../../installation/prerequisites/file-system/overview.md).

1. 切换到以下目录：

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   例如，如果应用程序安装在 `/var/www/html`，则 `settings.xml.dist` 文件位于以下目录之一：

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. 创建 `settings.xml` 文件，运行：

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. 在中进行更改 `settings.xml`.

1. 要指定用于映射的设置文件的新名称，请更改 `<settings_map_file>` 标记中 `path/to/config.xml` 文件。

欲知更多详情，请参见 [设置迁移模式](../technical-specification.md#settings-migration-mode) 工具的部分 [规范](../technical-specification.md).

## 下一个迁移步骤

* [迁移数据](data.md)
