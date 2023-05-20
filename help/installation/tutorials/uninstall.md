---
title: 解除安裝或重新安裝Adobe Commerce
description: 請依照下列步驟，解除安裝並重新安裝Adobe Commerce和Magento Open Source的內部部署。
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# 解除安裝或重新安裝Adobe Commerce

在使用這些指令之前，您必須 [安裝應用程式](../tutorials/install.md).

## 更新應用程式

若要更新應用程式：

* 如果您是從封存安裝軟體，或是使用「composer-create-project」，請參閱 [升級指南](../../upgrade/overview.md).
* 如果您是參與開發人員(也就是說，您使用的是 `git clone`)，請參閱 [更新應用程式](../../upgrade/developer/git-installs.md).

## 重新安裝應用程式

從命令列重新安裝應用程式的方式取決於您的角色：

* 如果您是從封存安裝軟體，或如果您使用「composer-create-project」，請參閱 [更新安裝相依性](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* 如果您是參與開發人員(也就是說，您已開始使用 `git clone`)，請參閱 [更新安裝相依性](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 解除安裝應用程式

解除安裝應用程式會刪除及還原資料庫、移除部署設定，並清除以下目錄： `var`.

若要解除安裝應用程式，請輸入下列命令：

```bash
bin/magento setup:uninstall
```

系統會顯示下列訊息，確認解除安裝成功：

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## 選擇性地保留產生的檔案

依預設， `bin/magento setup:upgrade` 清除編譯的程式碼和快取。 通常您會使用 `bin/magento setup:upgrade` 更新元件，每個元件可能需要不同的編譯類別。

但是，在某些情況下（特別是部署到生產環境），您可能希望避免清除編譯的程式碼，因為這可能需要一些時間。 （快取仍會清除。） 更新資料庫架構和資料 *不含* 清除編譯的程式碼，請輸入：

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>選填 `--keep-generated` 選項應由經驗豐富的系統整合經銷商在有限的情況下使用 *僅限*. 此選項應 *從不* 用於開發環境中。 不當使用此選用引數可能會在程式碼執行期間導致錯誤。

## 安裝應用程式

* [使用命令列安裝](../advanced.md)
