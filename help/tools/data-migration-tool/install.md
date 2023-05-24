---
title: 安装 [!DNL Data Migration Tool]
description: 了解如何安装 [!DNL Data Migration Tool] 在Magento1和Magento2之间传输数据。
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# 安装 [!DNL Data Migration Tool]

>[!INFO]
>
>Magento和的版本 [!DNL Data Migration Tool] 必须匹配。


确保使用 *同一发布版本* Magento2和 [!DNL Data Migration Tool]. 例如，对于Magento版本2.2.0，还必须使用 [!DNL Data Migration Tool] 版本2.2.0。

## 检查您的版本

使用以下方法之一验证您的Magento版本：

- [Composer](#composer-metapackage)
- [GitHub存储库](#github-repository)

### Composer中继包

如果使用Composer元包下载Magento软件，请输入以下命令：

```bash
php <magento_root>/bin/magento --version
```

### GitHub存储库

如果克隆Magento2 GitHub存储库，请输入以下命令：

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

如果您当前在 `develop` 分支，则必须更改为 [已发布分支](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) 然后再继续。

如果您尚未安装Adobe Commerce或Magento Open Source软件， [立即安装](../../installation/prerequisites/commerce.md).
如果要克隆GitHub存储库，请确保签出了版本标记，如中所述 [（参与者）克隆GitHub存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## 查找的已发布版本 [!DNL Data Migration Tool]

转到 [版本](https://github.com/magento/data-migration-tool/releases) 第页，共 [!DNL Data Migration Tool] GitHub存储库，查找可用的已发布版本。

## 安装 [!DNL Data Migration Tool]

您可以安装 [!DNL Data Migration Tool] 从：

- [&#39;repo.magento.com&#39;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

安装之前，请确保您具有：

- 已完成中提到的所有任务 [前提条件](prerequisites.md) 部分
- [已验证版本](install.md#check-your-version) Magento2软件的

### 安装自 `repo.magento.com`

安装 [!DNL Data Migration Tool]，您必须更新 `composer.json` 在Magento根安装目录中，提供 [!DNL Data Migration Tool] 包。

1. 以或切换至以下身份登录到应用程序服务器： [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 切换到应用程序根目录。
1. 输入以下命令：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   位置 `<version>` 必须匹配Magento2代码库的版本。

   例如，对于版本2.2.0，输入：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. 出现提示时，输入您的 [身份验证密钥](../../installation/prerequisites/authentication-keys.md). 您的公钥是您的用户名；您的私钥是您的密码。

### 从GitHub安装

如果您已克隆GitHub存储库，请按照以下步骤安装 [!DNL Data Migration Tool].

1. 以或切换至以下身份登录到应用程序服务器： [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 切换到应用程序根目录。
1. 输入以下命令：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   位置 `<version>` 必须匹配Magento2代码库的版本。

   例如，对于版本2.2.0，输入：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### 检查已安装的版本 [!DNL Data Migration Tool]

1. 更改为您的 [!DNL Data Migration Tool] 目录： `<vendor>/magento/data-migration-tool`.

1. 打开 [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) 在文本编辑器中。

1. 此 `version` 该文件中的条目是 [!DNL Data Migration Tool].
