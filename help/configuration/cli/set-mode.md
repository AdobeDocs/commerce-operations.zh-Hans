---
title: 設定操作模式
description: 閱讀設定Adobe Commerce操作模式的相關資訊。
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# 設定操作模式

{{file-system-owner}}

為了提高安全性和易用性，我們新增了切換命令 [應用程式模式](../bootstrap/application-modes.md) 從開發人員到生產環境，反之亦然。

生產模式的效能較佳，因為靜態檢視檔案會填入 `pub/static` 目錄和，因為程式碼編譯。

>[!INFO]
>
>在2.0.6版及更新版本中，當您在預設、開發和生產模式之間切換時，Commerce不會明確設定檔案或目錄許可權。 與其他模式不同，開發人員和生產模式設定在 `env.php` 檔案。 雲端基礎結構上的Adobe Commerce僅支援生產和維護模式。
>
>另請參閱 [開發和生產中的商務擁有權和許可權](../deployment/file-system-permissions.md).

當您變更為開發人員或生產模式時，我們會清除以下目錄的內容：

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

例外：

- `.htaccess` 未移除檔案
- `pub/static` 包含指定靜態內容版本的檔案；此檔案未移除

>[!INFO]
>
>依預設，Commerce會使用 `var` 目錄以儲存快取、記錄檔和編譯的程式碼。 您可以自訂此目錄，但在本指南中，假設為 `var`.

## 顯示目前模式

最簡單的方法是執行此命令，做為 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md). 如果您有共用託管，這是提供者可讓您登入伺服器的使用者。 如果您有私人伺服器，它通常是Commerce伺服器上的本機使用者帳戶。

命令使用方式：

```bash
bin/magento deploy:mode:show
```

系統會顯示類似下列的訊息：

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

其中：

- **`{mode}`** 可以是 `default`， `developer`，或 `production`

## 變更模式

命令使用方式：

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

其中：

- **`{mode}`** 為必填，可以是 `developer` 或 `production`

- **`--skip-compilation`** 是您可用來略過的選用引數 [程式碼編譯](../cli/code-compiler.md) 當您變更為生產模式時。

範例如下。

### 變更為生產模式

```bash
bin/magento deploy:mode:set production
```

類似下列顯示的訊息：

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or Sass files
CSS deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### 變更為開發人員模式

當您從生產模式變更為開發人員模式時，應清除產生的類別和物件管理員實體（如代理），以避免意外的錯誤。 之後，您可以變更模式。 使用下列步驟：

1. 如果您要從生產模式變更為開發人員模式，請刪除 `generated/code` 和 `generated/metadata` 目錄：

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. 設定模式：

   ```bash
   bin/magento deploy:mode:set developer
   ```

   系統會顯示下列訊息：

   ```terminal
   Enabled developer mode.
   ```

### 變更為預設模式

```bash
bin/magento deploy:mode:set default
```

系統會顯示下列訊息：

```terminal
Enabled default mode.
```

### 隨處執行CLI命令

[隨處執行CLI命令](../cli/config-cli.md#config-install-cli-first).

如果您尚未新增 `<Commerce-install-directory>/bin` 至您的系統 `PATH`，則單獨執行命令時可能會發生錯誤。
