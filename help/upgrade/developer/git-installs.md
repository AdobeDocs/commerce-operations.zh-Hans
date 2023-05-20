---
title: 升級Git安裝
description: 升級您從Git存放庫複製的Adobe Commerce或Magento Open Source安裝。
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# 升級Git安裝

本主題說明投稿開發人員如何在不重新安裝的情況下更新Adobe Commerce或Magento Open Source。 如果您不是參與開發人員，請參閱 [執行升級](../implementation/perform-upgrade.md).

如果您是參與開發人員，若要升級：

{{$include /help/_includes/server-login.md}}

1. 儲存您對所做的任何變更 `composer.json` 檔案，因為後續步驟會加以覆寫。

1. 建立備份 `composer.json` 檔案。

   ```bash
   cp composer.json composer.json.old
   ```

1. 更新您的本機存放庫以取得最新的程式碼：

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >若 `git pull origin develop` 失敗，請參閱 [疑難排解](https://support.magento.com/hc/en-us/articles/360034229872).

1. 比較並合併 `composer.json.old` 檔案包含 `composer.json` 檔案。

1. 解決相依性並將確切版本寫入 `composer.lock` 檔案。

   ```bash
   composer update
   ```

1. 更新資料庫：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```
