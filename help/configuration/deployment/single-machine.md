---
title: 單一電腦部署
description: 瞭解如何使用命令列在生產伺服器上將Commerce的更新部署。
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# 單一電腦部署

本主題提供使用命令列在生產伺服器上部署Commerce更新的指示。 此程式適用於負責在已安裝某些主題和區域設定的單一機器上執行商店的技術使用者。

## 假設

- 您已使用安裝Commerce [Composer](../../installation/composer.md).
- 您正在將更新直接套用至伺服器。

>[!WARNING]
>
>若您使用，本指南不適用 `git clone` 以安裝Commerce。
>投稿開發人員應使用 [本指南][install] 更新其Commerce安裝。

## 部署步驟

1. 以或切換至身分登入您的生產伺服器， [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).

1. 將目錄變更為Commerce基底目錄：

   ```bash
   cd <Commerce base directory>
   ```

1. 使用命令啟用維護模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 使用以下命令模式將更新套用至Commerce或其元件：

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **封裝**：您要更新的套件名稱。

   例如：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **版本**：您要更新的套裝軟體的目標版本。

1. 使用Composer更新元件：

   ```bash
   composer update
   ```

1. 更新資料庫結構和資料：

   ```bash
   bin/magento setup:upgrade
   ```

1. 編譯程式碼：

   ```bash
   bin/magento setup:di:compile
   ```

1. 部署靜態內容：

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```

1. 結束維護模式：

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
