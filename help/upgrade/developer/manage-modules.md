---
title: 管理模組和擴充功能（開發人員）
description: 使用命令列介面和撰寫器封裝管理員來管理Adobe Commerce和Magento Open Source模組及擴充功能。
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---

# 管理模組和擴充功能

貢獻者開發人員透過在Adobe Commerce或Magento Open Source中指定其版本來升級模組和擴充功能 `composer.json` 檔案。 如果您不是參與開發人員，請參閱 [執行升級](../implementation/perform-upgrade.md).

您可以新增 `require` 區段至 `composer.json` 檔案或您可以使用 `composer require` 命令，如下所示：

{{$include /help/_includes/server-login.md}}

您有以下選項：

## 取得可用的模組版本

命令使用方式：

```bash
composer show --all <vendor>/<name>
```

例如：

```bash
composer show --all example/module
```

## 使用 `composer require` 命令

命令使用方式：

```bash
composer require <vendor>/<name>:<version>
```

例如：

```bash
composer require example/module:1.0.0
```

Composer正在更新相依性並安裝模組，請稍候。

## 新增 `require` composer.json檔案的區段

1. 開啟 `composer.json` 在文字編輯器中。

1. 新增 `require` 區段。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 將變更儲存至 `composer.json` 檔案並退出文字編輯器。

1. 解決相依性並將確切版本寫入 `composer.lock` 檔案。

   ```bash
   composer update
   ```
