---
title: 升级[!DNL Data Migration Tool]
description: 了解如何升级[!DNL Data Migration Tool]以在Magento 1和Magento 2之间传输数据。
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%
---
# 升级[!DNL Data Migration Tool]

要确保当前Magento 2安装的版本与[!DNL Data Migration Tool]完全匹配，您可能需要升级该工具。

## 先决条件

升级[!DNL Data Migration Tool]之前，您必须：

* 升级Magento软件以获得最新版本

* 备份`vendor/magento/data-migration-tool`目录

* 确保[!DNL Data Migration Tool]版本与Magento应用程序版本匹配

### 升级Magento软件

如果您尚未这样做，请[升级Magento软件](../../upgrade/overview.md)。

### 备份`vendor/magento/data-migration-tool`目录

在升级[!DNL Data Migration Tool]之前，请至少备份`vendor/magento/data-migration-tool`目录。 在升级期间，可以删除该代码并将其替换为更新的代码。

您还可以使用以下命令备份整个Magento代码库和数据库：

```shell
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>`vendor/magento/data-migration-tool`目录包含您的自定义代码。 无法备份它意味着在升级过程中可能会丢失自定义项。


### 确保版本匹配

[!DNL Data Migration Tool]和您的Magento软件的版本必须完全匹配。 例如，Magento 2.1.2需要[!DNL Data Migration Tool]的版本2.1.2。

请参阅[安装 [!DNL Data Migration Tool]](install.md)主题以了解如何：

* [检查](install.md#check-your-version)您的Magento 2版本

* [查找[!DNL Data Migration Tool]的已发布版本](install.md#find-released-versions-of-data-migration-tool)

* [检查](install.md#check-version-of-installed-data-migration-tool) [!DNL Data Migration Tool]版本

## 升级[!DNL Data Migration Tool]

1. 以[文件系统所有者](../../installation/prerequisites/file-system/overview.md)身份登录或切换到您的应用程序服务器。
1. 切换到应用程序根目录。
1. 输入以下命令：

   ```shell
   composer require magento/data-migration-tool:<version>
   ```

   其中`<version>`必须匹配Magento 2代码库的版本。

   例如，对于版本2.1.2，输入：

   ```shell
   composer require magento/data-migration-tool:2.1.2
   ```

1. 等待命令完成。
