---
title: 安装 [!DNL Data Migration Tool]
description: 了解如何安装 [!DNL Data Migration Tool] 在Magento1和Magento2之间传输数据。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 安装 [!DNL Data Migration Tool]

>[!INFO]
>
>Magento和 [!DNL Data Migration Tool] 必须匹配。


确保您使用 *同一已发布版本* Magento2和 [!DNL Data Migration Tool]. 例如，对于Magento版本2.2.0，您还必须使用 [!DNL Data Migration Tool] 版本2.2.0。

## 检查您的版本

使用以下方法验证您的Magento版本：

- [编辑器](#composer-metapackage)
- [GitHub存储库](#github-repository)

### 编辑器元包

如果您使用 [编辑器](https://glossary.magento.com/composer) metapackage，输入以下命令：

```bash
php <magento_root>/bin/magento --version
```

### GitHub存储库

如果您克隆了Magento2 GitHub存储库，请输入以下命令：

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

如果您当前在 `develop` 分支，必须更改为 [释放分支](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) 之前。

如果您尚未安装Adobe Commerce或Magento Open Source软件， [立即安装](../../installation/prerequisites/commerce.md).
如果要克隆GitHub存储库，请确保按 [（参与者）克隆GitHub存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## 查找的已发布版本 [!DNL Data Migration Tool]

转到 [版本](https://github.com/magento/data-migration-tool/releases) 页面 [!DNL Data Migration Tool] 用于查找可用已发布版本的GitHub存储库。

## 安装 [!DNL Data Migration Tool]

您可以安装 [!DNL Data Migration Tool] 从：

- [&#39;repo.magento.com&#39;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

安装之前，请确保您具有：

- 已完成 [先决条件](prerequisites.md) 部分
- [已验证版本](install.md#check-your-version) Magento2软件

### 安装自 `repo.magento.com`

安装 [!DNL Data Migration Tool]，您必须更新 `composer.json` 在Magento根安装目录中提供 [!DNL Data Migration Tool] 包。

1. 作为或切换到 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 更改到应用程序根目录。
1. 输入以下命令：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   其中 `<version>` 必须匹配Magento2代码库的版本。

   例如，对于版本2.2.0，输入：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. 出现提示时，输入 [身份验证密钥](../../installation/prerequisites/authentication-keys.md). 您的公钥是您的用户名；您的私钥是您的密码。

### 从GitHub安装

如果已克隆GitHub存储库，请按照以下步骤安装 [!DNL Data Migration Tool].

1. 作为或切换到 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 更改到应用程序根目录。
1. 输入以下命令：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   where `<version>` 必须匹配Magento2代码库的版本。

   例如，对于版本2.2.0，输入：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### 检查已安装的版本 [!DNL Data Migration Tool]

1. 更改为 [!DNL Data Migration Tool] 目录： `<vendor>/magento/data-migration-tool`.

1. 打开 [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) 在文本编辑器中。

1. 的 `version` 该文件中的条目是 [!DNL Data Migration Tool].
