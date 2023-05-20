---
title: 升級資料庫結構和資料
description: 請依照下列步驟升級Adobe Commerce或Magento Open Source資料庫架構。
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# 升級資料庫結構和資料

使用此指令之前，您必須 [安裝應用程式](../advanced.md).

## 升級資料庫結構和資料

每當您執行導致資料庫結構描述或資料變更的動作時，都必須執行本節中討論的命令來更新它們。 原因的部份清單如下：

* 您使用命令列升級應用程式
* 您使用命令列安裝或更新了元件
* 您使用命令列啟用或停用元件

>[!NOTE]
>
>A *元件* 可以是模組、主題或語言套件；元件是否來自Commerce Marketplace並不重要。

1. 開始升級：

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   位置 `--keep-generated` 是不會更新的選用引數 [靜態檢視檔案](../../configuration/cli/static-view-file-deployment.md). 此選用引數可供使用 *僅限* 在有限的情況下，由經驗豐富的系統整合經銷商提供。 該使用 *僅限* 在 [生產模式](../../configuration/bootstrap/application-modes.md#production-mode). 它應該 *not* 用於 [開發人員模式](../../configuration/bootstrap/application-modes.md#developer-mode).

1. 清除快取：

   ```bash
   bin/magento cache:clean
   ```
