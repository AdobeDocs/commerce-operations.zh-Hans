---
title: 数据迁移设置
description: 了解如何使用 [!DNL Data Migration Tool]开始将设置从Magento1迁移到Magento2。
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 数据迁移设置

`Settings`模式迁移商店、网站和系统配置，如运费、付款和税务设置。 根据我们的数据迁移[订单](overview.md#migration-order)，您应该先迁移设置。

在开始之前，请执行以下步骤进行准备：

1. 以[文件系统所有者](../../../installation/prerequisites/file-system/overview.md)的身份登录到应用程序服务器。

1. 更改为`/bin`目录或确保将其添加到您的系统`PATH`。

>[!NOTE]
>
>确保Magento2以`default`模式部署。 开发人员模式可能会导致迁移工具中出现验证错误。


有关更多详细信息，请参阅[首要步骤](overview.md#first-steps)部分。

## 运行设置迁移命令

要开始迁移设置，请运行：

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]`是从头开始迁移的可选参数。 可以使用此参数测试迁移

* `[-a|--auto]`是一个可选参数，当遇到完整性检查错误时，它可阻止停止迁移。

* `{<path to config.xml>}`是迁移工具[`config.xml`](../configure.md#configure-migration-in-vendor-folder)文件的绝对文件系统路径；此参数是必需的。

>[!NOTE]
>
>此命令不会迁移所有配置设置。 在继续之前，请验证Magento2管理员中的所有设置。


成功传输设置后将显示`Migration completed`消息。

## 配置自定义迁移规则

迁移设置时，可以忽略、重命名或更改系统配置。 为此，请在`settings.xml`文件中指定自定义规则。

1. 以[文件系统所有者](../../../installation/prerequisites/file-system/overview.md)的身份登录或切换到应用程序服务器。

1. 切换到以下目录：

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   例如，如果应用程序安装在`/var/www/html`中，则`settings.xml.dist`文件位于以下目录之一：

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. 要从提供的示例创建`settings.xml`文件，请运行：

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. 在`settings.xml`中进行更改。

1. 要指定用于映射的设置文件的新名称，请更改`path/to/config.xml`文件中的`<settings_map_file>`标记。

有关更多详细信息，请参阅工具[规范](../technical-specification.md)的[设置迁移模式](../technical-specification.md#settings-migration-mode)部分。

## 下一个迁移步骤

* [迁移数据](data.md)
