---
title: 建立指向LESS檔案的符號連結
description: 瞭解如何建立LESS檔案的符號連結。
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# 建立指向LESS檔案的符號連結

{{file-system-owner}}

若要建立LESS檔案的符號連結：

命令選項：

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>在開發期間，這個指令會為LESS檔案建立符號連結 `var/view_preprocessed` 和 `pub/static` 資料夾。 此程式不會將LESS檔案編譯成CSS檔案。

下表說明此命令的引數和值。

| 引數 | 值 | 必填？ |
| --------- | ----- | --------- |
| `--type` | 來源檔案型別： [更少] （預設值：「less」）<br>目前LESS是唯一支援的檔案型別。 | 否 |
| `--locale` | 地區代碼。<br>若要顯示地區代碼清單，請輸入 `bin/magento info:language:list` | 否 |
| `--area` | 區域(`adminhtml` 管理區域， `frontend` （適用於店面）。 | 否 |
| `--theme` | 中的主題名稱 `<VendorName>/<theme-name>` 格式。 例如， `Magento/blank` 或 `Magento/backend`. | 否 |
| `<file>` | 要轉換為不含CSS副檔名的LESS的CSS檔案清單（以空格分隔）。 (預設為 `css/styles-m css/styles-l`，若為admin型別 `css/styles css/styles-old`) | 否 |

例如，為名為的前端主題建立LESS檔案 `VendorName/themeName` 在 `en_US` 使用名為的CSS檔案的地區設定 `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`，輸入下列命令：

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

下列訊息會顯示以確認成功：

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

若要為管理員建立LESS檔案：

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
