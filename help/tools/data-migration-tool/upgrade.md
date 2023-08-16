---
title: 升级 [!DNL Data Migration Tool]
description: 了解如何升级 [!DNL Data Migration Tool] 在Magento1和Magento2之间传输数据。
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 升级 [!DNL Data Migration Tool]

要确保当前Magento2安装的版本和 [!DNL Data Migration Tool] 完全匹配，您可能需要升级该工具。

## 先决条件

升级之前 [!DNL Data Migration Tool]，您必须：

* 升级Magento软件以获取最新版本

* 备份 `vendor/magento/data-migration-tool` 目录

* 确保 [!DNL Data Migration Tool] 版本与Magento应用程序版本匹配

### 升级Magento软件

如果你还没有这么做的话， [升级Magento软件](../../upgrade/overview.md).

### 备份 `vendor/magento/data-migration-tool` 目录

升级之前 [!DNL Data Migration Tool]，至少备份 `vendor/magento/data-migration-tool` 目录。 在升级期间，可以删除该代码并将其替换为更新的代码。

您还可以使用以下命令备份整个Magento代码库和数据库：

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>此 `vendor/magento/data-migration-tool` 目录包含您的自定义代码。 无法备份它意味着在升级过程中可能会丢失自定义项。


### 确保版本匹配

的版本 [!DNL Data Migration Tool] 并且您的Magento软件必须完全匹配。 例如，Magento2.1.2需要版本2.1.2的 [!DNL Data Migration Tool].

请参阅 [安装 [!DNL Data Migration Tool]](install.md) 要了解如何执行以下操作：

* [Check](install.md#check-your-version) Magento2版本

* [查找](install.md#find-released-versions-of-data-migration-tool) 的已发布版本 [!DNL Data Migration Tool]

* [Check](install.md#check-version-of-installed-data-migration-tool) 该 [!DNL Data Migration Tool] 版本

## 升级 [!DNL Data Migration Tool]

1. 以以下身份登录到您的应用程序服务器，或切换到 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 切换到应用程序根目录。
1. 输入以下命令：

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   位置 `<version>` 必须匹配Magento2代码库的版本。

   例如，对于版本2.1.2，输入：

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. 等待命令完成。
