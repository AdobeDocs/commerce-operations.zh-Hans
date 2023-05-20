---
title: 程式碼編譯器
description: 瞭解如何從命令列執行程式碼編譯器。
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# 程式碼編譯器

{{file-system-owner}}

程式碼編譯包含下列內容（並無特定順序）：

- 應用程式程式碼產生（工廠、代理）
- 區域設定彙總（每個區域最佳化的相依性插入設定）
- 攔截器產生（最佳化的攔截器程式碼產生）
- 攔截快取產生
- 存放庫程式碼產生（為API產生的程式碼）
- 服務資料屬性產生（為資料物件產生的擴充功能類別）

您可以在下列位置找到程式碼編譯類別： [\Magento\Setup\Module\Di\App\Task\Operation][operation] 名稱空間。

若要執行單一租使用者編譯器：

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

若要在安裝Commerce應用程式之前編譯程式碼：

在某些情況下，您可能需要在安裝Commerce應用程式之前編譯程式碼。

1. 啟用模組。

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   使用 `[-c|--clear-static-content]` 清除靜態內容的選項。 如果您先前已啟用或停用模組，且必須清除先前為其產生的靜態內容，則必須執行此動作。

   另請參閱 [啟用模組](../../installation/tutorials/manage-modules.md).

1. 編譯程式碼。

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

若要在不使用資料庫的情況下編譯程式碼，請參閱 [部署靜態檢視檔案而不安裝Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
