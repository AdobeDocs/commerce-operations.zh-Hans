---
title: 安装 [!DNL Data Migration Tool]
description: 了解如何安装 [!DNL Data Migration Tool] 以在Magento 1和Magento 2之间传输数据。
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# 安装[!DNL Data Migration Tool]

>[!INFO]
>
>Magento和[!DNL Data Migration Tool]的版本必须匹配。


确保您同时使用Magento 2和&#x200B;*的*&#x200B;相同发布版本[!DNL Data Migration Tool]。 例如，对于Magento版本2.2.0，还必须使用[!DNL Data Migration Tool]版本2.2.0。

## 检查您的版本

使用以下方法之一验证您的Magento版本：

- [Composer](#composer-metapackage)
- [GitHub存储库](#github-repository)

### Composer中继包

如果您使用Composer元包下载了Magento软件，请输入以下命令：

```bash
php <magento_root>/bin/magento --version
```

### GitHub存储库

如果克隆了Magento 2 GitHub存储库，请输入以下命令：

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

如果您当前在`develop`分支中，则必须更改为[已发布的分支](https://developer.adobe.com/commerce/contributor/guides/install/change-version)，然后才能继续。

如果尚未安装Adobe Commerce软件，请[立即安装](../../installation/prerequisites/commerce.md)。
如果要克隆GitHub存储库，请确保签出[（参与者）克隆GitHub存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)中讨论的版本标记。

## 查找[!DNL Data Migration Tool]的已发布版本

转到[&#x200B; GitHub存储库的](https://github.com/magento/data-migration-tool/releases)版本[!DNL Data Migration Tool]页面以查找可用的发布版本。

## 安装[!DNL Data Migration Tool]

您可以从以下位置安装[!DNL Data Migration Tool]：

- [&#39;repo.magento.com&#39;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

安装之前，请确保您拥有：

- 已完成[前提条件](prerequisites.md)部分中提到的所有任务
- [已验证Magento 2软件的版本](install.md#check-your-version)

### 从`repo.magento.com`安装

要安装[!DNL Data Migration Tool]，您必须在Magento根安装目录中更新`composer.json`以提供[!DNL Data Migration Tool]包的位置。

1. 以[文件系统所有者](../../installation/prerequisites/file-system/overview.md)的身份登录或切换到您的应用程序服务器。
1. 切换到应用程序根目录。
1. 输入以下命令：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   其中`<version>`必须与Magento 2代码库的版本匹配。

   例如，对于版本2.2.0，输入：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. 出现提示时，输入您的[身份验证密钥](../../installation/prerequisites/authentication-keys.md)。 您的公钥是您的用户名；您的私钥是您的密码。

### 从GitHub安装

如果您已克隆GitHub存储库，请按照以下步骤安装[!DNL Data Migration Tool]。

1. 以[文件系统所有者](../../installation/prerequisites/file-system/overview.md)的身份登录或切换到您的应用程序服务器。
1. 切换到应用程序根目录。
1. 输入以下命令：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   其中`<version>`必须与Magento 2代码库的版本匹配。

   例如，对于版本2.2.0，输入：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### 检查已安装的[!DNL Data Migration Tool]的版本

1. 更改到[!DNL Data Migration Tool]目录： `<vendor>/magento/data-migration-tool`。

1. 在文本编辑器中打开[`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json)。

1. 该文件中的`version`条目是[!DNL Data Migration Tool]的版本。
