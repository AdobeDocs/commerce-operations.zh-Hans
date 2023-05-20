---
title: 常用命令
description: 檢視常見Commerce CLI命令和用法的取樣。
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 常用命令

以下摘要說明一些可用的命令。

**顯示完整的命令清單**：

```bash
bin/magento list
```

說明命令範例：

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

命令僅以摘要形式顯示；如需命令的詳細資訊，請按一下「命令」欄中的連結。

| 命令 | 說明 |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | 管理快取 |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | 管理索引器 |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | 執行Commerce cron工作 |
| [`magento setup:di:compile`](../cli/code-compiler.md) | 編譯所有不存在的代理程式和工廠；並預先編譯一個商店和網站的類別定義、繼承資訊和外掛程式定義。 |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | 模組相依性、循環相依性和Commerce框架相依性。 |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | 建立翻譯字典或翻譯套件 |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | 部署靜態檢視檔案 |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | 從較少專案建立CSS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | 執行自動化測試 |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | 更新您的版面XML檔案，以符合新的可延伸樣式表語言轉換(XSLT)樣式表 |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | 產生資料以用於效能測試。 |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | 安裝Commerce應用程式後安裝選用的範例資料。<br><br>如需有關範例資料的詳細資訊，請參閱 [選擇性範例資料](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | 管理後端設定 |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | 建立/編輯/解除鎖定管理員使用者。 |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | 啟用/停用開發人員範本提示。 |

## 通用引數

以下引數是所有命令通用的引數。 這些命令可以在安裝Commerce軟體之前或之後執行：

| 詳細版本 | 簡短版本 | 含義 |
|--- |--- |--- |
| `--help` | `-h` | 取得任何命令的說明。 例如， `./magento help setup:install` 或 `./magento help setup:config:set`. |
| `--quiet` | `-q` | 安靜模式；無輸出。 |
| `--no-interaction` | `-n` | 無互動式問題。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細程度。 例如， `--verbose=3` 或 `-vvv` 顯示除錯詳細資訊，這是最詳細的輸出。 預設為 `--verbose=1` 或 `-v`. |
| `--version` | `-V` | 顯示此應用程式版本 |
| `--ansi` | 不適用 | 強制ANSI輸出 |
| `--no-ansi` | 不適用 | 停用ANSI輸出 |
