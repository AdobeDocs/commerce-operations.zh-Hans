---
title: 安裝 [!DNL Data Migration Tool]
description: 瞭解如何安裝 [!DNL Data Migration Tool] 以在Magento1和Magento2之間傳輸資料。
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# 安裝 [!DNL Data Migration Tool]

>[!INFO]
>
>Magento和的版本 [!DNL Data Migration Tool] 必須相符。


請確定您使用 *相同發行版本* Magento2和 [!DNL Data Migration Tool]. 例如，對於Magento版本2.2.0，您也必須使用 [!DNL Data Migration Tool] 版本2.2.0。

## 檢查您的版本

使用以下其中一種方法來驗證您的Magento版本：

- [Composer](#composer-metapackage)
- [GitHub存放庫](#github-repository)

### Composer中繼套件

如果您使用Composer中繼資料下載Magento軟體，請輸入下列命令：

```bash
php <magento_root>/bin/magento --version
```

### GitHub存放庫

如果您複製Magento2 GitHub存放庫，請輸入下列命令：

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

如果您目前在 `develop` 分支，您必須變更為 [已發行分支](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) 然後再繼續。

如果您尚未安裝Adobe Commerce或Magento Open Source軟體， [立即安裝](../../installation/prerequisites/commerce.md).
如果您要複製GitHub存放庫，請務必取出版本標籤，如中所述 [（貢獻者）複製GitHub存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## 尋找的發行版本 [!DNL Data Migration Tool]

前往 [發行版本](https://github.com/magento/data-migration-tool/releases) 第頁/ [!DNL Data Migration Tool] GitHub存放庫以尋找可用的發行版本。

## 安裝 [!DNL Data Migration Tool]

您可以安裝 [!DNL Data Migration Tool] 從：

- [&#39;repo.magento.com&#39;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

安裝之前，請確定您擁有：

- 已完成「 」中提到的所有工作 [先決條件](prerequisites.md) 區段
- [已驗證版本](install.md#check-your-version) Magento2軟體的

### 安裝來源 `repo.magento.com`

若要安裝 [!DNL Data Migration Tool]，您必須更新 `composer.json` 在Magento根安裝目錄中，提供 [!DNL Data Migration Tool] 封裝。

1. 以或切換至以下身分登入應用程式伺服器： [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 變更至應用程式根目錄。
1. 輸入下列命令：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   位置 `<version>` 必須與Magento2程式碼基底的版本相符。

   例如，對於2.2.0版，請輸入：

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. 出現提示時，輸入您的 [驗證金鑰](../../installation/prerequisites/authentication-keys.md). 您的公開金鑰是您的使用者名稱；您的私密金鑰是您的密碼。

### 從GitHub安裝

如果您已複製GitHub存放庫，請依照下列步驟安裝 [!DNL Data Migration Tool].

1. 以或切換至以下身分登入應用程式伺服器： [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 變更至應用程式根目錄。
1. 輸入下列命令：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   位置 `<version>` 必須與Magento2程式碼基底的版本相符。

   例如，對於2.2.0版，請輸入：

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### 檢查已安裝的版本 [!DNL Data Migration Tool]

1. 變更為您的 [!DNL Data Migration Tool] 目錄： `<vendor>/magento/data-migration-tool`.

1. 開啟 [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) 在文字編輯器中。

1. 此 `version` 該檔案中的專案是 [!DNL Data Migration Tool].
