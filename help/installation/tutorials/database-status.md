---
title: 檢查資料庫狀態
description: 請依照下列步驟檢查Adobe Commerce或Magento Open Source資料庫狀態。
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 2%

---

# 檢查資料庫狀態

在執行這個命令之前，您必須 [建立或更新部署設定](deployment.md).

## 命令使用方式

檢查資料庫的狀態。

```bash
bin/magento setup:db:status
```

這個命令沒有引數或選項。

範例輸出如下：

```terminal
All modules are up to date.
```

該命令會傳回下列其中一個退出代碼：

| 退出代碼 | 說明 | 建議的動作 |
|--------------|--------------|---------------|
| 0 | 一般 | 無 |
| 1 | 某些模組使用比資料庫更新或舊的程式碼版本 | 執行 [`magento setup:upgrade`](database-upgrade.md) 更新資料庫結構描述並執行 `composer update` 從應用程式根目錄更新元件相依性 |
| 2 | `magento setup:upgrade` 為必填 | [`magento setup:upgrade`](database-upgrade.md) 更新資料庫綱要 |
