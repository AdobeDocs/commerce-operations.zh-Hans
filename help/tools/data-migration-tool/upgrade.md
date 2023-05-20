---
title: 升級 [!DNL Data Migration Tool]
description: 瞭解如何升級 [!DNL Data Migration Tool] 以在Magento1和Magento2之間傳輸資料。
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 升級 [!DNL Data Migration Tool]

若要確認您目前的Magento2安裝版本及 [!DNL Data Migration Tool] 完全符合，您可能需要升級工具。

## 必要條件

升級之前 [!DNL Data Migration Tool]，您必須：

* 升級您的Magento軟體以取得最新版本

* 備份 `vendor/magento/data-migration-tool` 目錄

* 請確定 [!DNL Data Migration Tool] 版本與Magento應用程式版本相符

### 升級您的Magento軟體

如果您尚未這麼做， [升級Magento軟體](../../upgrade/overview.md).

### 備份 `vendor/magento/data-migration-tool` 目錄

升級之前 [!DNL Data Migration Tool]，至少備份 `vendor/magento/data-migration-tool` 目錄。 在升級期間，可將其刪除並由更新的程式碼取代。

您也可以使用下列命令備份整個Magento程式碼基底和資料庫：

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>此 `vendor/magento/data-migration-tool` 目錄包含您的自訂程式碼。 若未備份，升級期間可能會遺失自訂內容。


### 確定版本相符

的版本 [!DNL Data Migration Tool] 而且您的Magento軟體必須完全符合。 例如，Magento2.1.2需要2.1.2版的 [!DNL Data Migration Tool].

請參閱 [安裝 [!DNL Data Migration Tool]](install.md) 要瞭解如何執行下列操作的主題：

* [Check](install.md#check-your-version) 您的Magento2版本

* [尋找](install.md#find-released-versions-of-data-migration-tool) 的發行版本 [!DNL Data Migration Tool]

* [Check](install.md#check-version-of-installed-data-migration-tool) 此 [!DNL Data Migration Tool] 版本

## 升級 [!DNL Data Migration Tool]

1. 以身分登入您的應用程式伺服器，或切換至 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 變更至應用程式根目錄。
1. 輸入下列命令：

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   位置 `<version>` 必須與Magento2程式碼基底的版本相符。

   例如，對於2.1.2版，請輸入：

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. 等待命令完成。
