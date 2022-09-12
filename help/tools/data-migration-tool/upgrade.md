---
title: 升级 [!DNL Data Migration Tool]
description: 了解如何升级 [!DNL Data Migration Tool] 在Magento1和Magento2之间传输数据。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# 升级 [!DNL Data Migration Tool]

确保当前Magento2安装的版本以及 [!DNL Data Migration Tool] 完全匹配，您可能需要升级该工具。

## 先决条件

升级之前 [!DNL Data Migration Tool]，您必须：

* 升级您的Magento软件以获取最新版本

* 备份 `vendor/magento/data-migration-tool` 目录

* 确保 [!DNL Data Migration Tool] 版本与Magento应用程序版本匹配

### 升级Magento软件

如果你还没这么做， [升级Magento软件](../../upgrade/overview.md).

### 备份 `vendor/magento/data-migration-tool` 目录

在升级之前 [!DNL Data Migration Tool]，至少备份 `vendor/magento/data-migration-tool` 目录访问Advertising Cloud的帮助。 在升级期间，可以删除该代码并将其替换为更新的代码。

您还可以使用以下命令备份整个Magento代码库和数据库：

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>的 `vendor/magento/data-migration-tool` 目录包含您的自定义代码。 无法备份它意味着您可能会在升级过程中丢失自定义设置。


### 确保版本匹配

的版本 [!DNL Data Migration Tool] 您的Magento软件必须完全匹配。 例如，Magento2.1.2要求使用 [!DNL Data Migration Tool].

请参阅 [安装 [!DNL Data Migration Tool]](install.md) 主题了解如何：

* [检查](install.md#check-your-version) 您的Magento2版本

* [查找](install.md#find-released-versions-of-data-migration-tool) 的已发布版本 [!DNL Data Migration Tool]

* [检查](install.md#check-version-of-installed-data-migration-tool) the [!DNL Data Migration Tool] 版本

## 升级 [!DNL Data Migration Tool]

1. 作为或切换到，登录到您的应用程序服务器 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 更改到应用程序根目录。
1. 输入以下命令：

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   where `<version>` 必须匹配Magento2代码库的版本。

   例如，对于版本2.1.2，输入：

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. 命令完成时等待。
