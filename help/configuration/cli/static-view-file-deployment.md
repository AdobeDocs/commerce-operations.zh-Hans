---
title: 部署靜態檢視檔案
description: 瞭解在生產模式期間將靜態檔案寫入Commerce檔案系統。
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---

# 部署靜態檢視檔案

{{file-system-owner}}

靜態檢視檔案部署命令可讓您在設定Commerce軟體時，將靜態檔案寫入Commerce檔案系統 [生產模式](../bootstrap/application-modes.md#production-mode).

詞語 _靜態檢視檔案_ 參考以下內容：

- 「靜態」表示它可以針對網站進行快取（也就是說，檔案不會動態產生）。 範例包括從LESS產生的影像和CSS。
- 「檢視」是指表示層（來自MVC）。

靜態檢視檔案位於 `<magento_root>/pub/static` 目錄，有些快取在 `<magento_root>/var/view_preprocessed` 目錄。

靜態檢視檔案部署會受應用程式模式影響，如下所示：

- [預設](../bootstrap/application-modes.md#default-mode) 和 [開發人員](../bootstrap/application-modes.md#developer-mode) 模式：Commerce會視需要產生模式，但其餘的會快取在檔案中，以提高存取速度。
- [生產](../bootstrap/application-modes.md#production-mode) 模式：靜態檔案為 _not_ 產生或快取。

您必須使用本主題中討論的命令，手動將靜態檢視檔案寫入Commerce檔案系統；之後，您可以限制許可權以限制漏洞，並防止意外或惡意覆寫檔案。

>[!WARNING]
>
>_僅限開發人員模式_：安裝或啟用新模組時，可能會載入新的JavaScript、CSS、版面配置等。 若要避免靜態檔案發生問題，您必須清除舊檔案，以確保取得新模組的所有變更。 您可以用數種方式清除產生的靜態檢視檔案。 請參閱 [清除靜態檔案快取主題以取得詳細資料](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) 以取得詳細資訊。

**若要部署靜態檢視檔案**：

1. 以或身分登入Commerce伺服器 [切換到檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
1. 刪除以下專案的內容 `<magento_root>/pub/static`，但以下專案除外： `.htaccess` 檔案。 請勿刪除此檔案。
1. 執行靜態檢視檔案部署工具 `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >如果您在「管理員」中啟用靜態檢視檔案合併， `pub/static` 目錄系統必須是可寫入的。

   命令選項：

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

下表說明此命令的引數和值。

| 選項 | 說明 | 必填？ |
| ------ | ----------- | --------- |
| `<languages>` | 以空格分隔的 [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) 要輸出靜態檢視檔案的語言代碼。 (預設為 `en_US`.)<br>執行以尋找清單： `bin/magento info:language:list` | 否 |
| `--language (-l)` | 只產生指定語言的檔案。 未指定選項的預設值是產生所有ISO-639語言代碼的檔案。 您可以一次指定一個語言代碼的名稱。 預設值為 **全部**.<br>例如： `--language en_US --language es_ES` | 否 |
| `--exclude-language` | 產生指定語言代碼的檔案。 預設為不排除任何專案，但未指定選項。 您可以指定一個語言代碼的名稱，或以逗號分隔的語言代碼清單。 預設值為 **無**. | 否 |
| `--theme <theme>` | 要部署靜態內容的主題。 預設值為 **全部**.<br>例如： `--theme Magento/blank --theme Magento/luma` | 否 |
| `--exclude-theme <theme>` | 部署靜態內容時要排除的主題。 預設值為 **無**.<br>例如， `--exclude-theme Magento/blank` | 否 |
| `--area (-a)` | 只產生指定區域的檔案。 未指定選項的預設值是為所有區域產生檔案。 有效值為 `adminhtml` 和 `frontend`. 預設值為 **全部**.<br>例如： `--area adminhtml` | 否 |
| `--exclude-area` | 不要產生指定區域的檔案。 預設為不排除任何專案，但未指定選項。 預設值為 **無**. | 否 |
| `--jobs (-j)` | 使用指定的作業數目啟用平行處理。 預設值為0 （不要在平行處理程式中執行）。 預設值為 **0**. | 否 |
| `--symlink-locale` | 為這些區域設定的檔案建立符號連結，這些檔案會傳遞以進行部署，但沒有自訂。 | 否 |
| `--content-version=CONTENT-VERSION` | 如果在多個節點上執行部署，可以使用靜態內容的自訂版本，以確保靜態內容版本相同且快取可正常運作。 | 否 |
| `--no-javascript` | 不要部署JavaScript檔案 | 否 |
| `--no-css` | 請勿部署CSS檔案。 | 否 |
| `--no-less` | 請勿部署LESS檔案。 | 否 |
| `--no-images` | 不要部署影像。 | 否 |
| `--no-fonts` | 不要部署字型檔案。 | 否 |
| `--no-html` | 請勿部署HTML檔案。 | 否 |
| `--no-misc` | 請勿部署其他型別的檔案：MD、JBF、CSV、JSON、TXT、HTC、SWF | 否 |
| `--no-html-minify` | 請勿將HTML檔案縮制。 | 否 |
| `-s <quick\|standard\|compact>` | 定義部署策略。 只有當您有多個本機時，才使用這些選項。<ul><li>使用 [快速策略](static-view-file-strategy.md#quick-strategy) 將部署時間縮到最短。 如果未指定，則這是預設的命令選項。</li><li>使用 [標準策略](static-view-file-strategy.md#standard-strategy) 以部署所有封裝的所有靜態檢視檔案。</li><li>使用 [壓縮策略](static-view-file-strategy.md#compact-strategy) 以節省伺服器上的磁碟空間。</li></ul> | 否 |
| `--no-parent` | 不要為目前主題的父主題產生檔案。 如果您未明確使用嘗試部署的目前主題的父主題，強烈建議您使用此標幟。 如此可大幅提升處理速度。 此標幟可在Commerce 2.4.2中使用 | 否 |
| `--force (-f)` | 以任何模式部署檔案。 (根據預設，靜態內容部署工具只能在生產模式下執行。 使用此選項可在預設或開發人員模式下執行)。 | 否 |

>[!INFO]
>
>如果您同時指定兩個值 `<languages>` 和 `--language`， `<languages>` 優先。

## 範例

以下是一些命令範例。

### 排除主題和HTML縮制

以下命令會為美式英文部署靜態內容(`en_US`)語言，排除Commerce提供的Luma主題，且不會縮制HTML檔案。

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

範例輸出：

```terminal
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

下列命令只會使用標準部署策略部署JavaScript （含4個工作）：

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

以下命令只會部署CSS和LESS，並包含3個工作和快速部署策略：

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### 產生一個主題和一個區域的靜態檢視檔案

以下命令為所有語言生成靜態檢視檔案，僅前端區域，僅Commerce Luma主題，不生成字型：

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

範例輸出：

```terminal
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## 部署靜態檢視檔案而不安裝Commerce

您可能想要在單獨的非生產環境中執行部署流程，以避免在敏感的生產機器上執行任何建置流程。

若要這麼做，請執行下列步驟：

1. 執行 [`bin/magento app:config:dump`](../cli/export-configuration.md) 以從您的生產系統匯出設定。
1. 將匯出的檔案複製到非生產程式碼基底。
1. 部署靜態檢視檔案： `bin/magento setup:static-content:deploy`

## 疑難排解靜態檢視檔案部署工具

[請先安裝Commerce軟體](../../installation/overview.md)；否則，您將無法執行靜態檢視檔案部署工具。

**症狀**：當您執行靜態檢視檔案部署工具時，會顯示下列錯誤：

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**解決方案**：

使用下列步驟：

1. 使用安裝Commerce軟體 [命令列](../../installation/composer.md).
1. 以或身分登入應用程式伺服器 [切換至](../../installation/prerequisites/file-system/overview.md)，即檔案系統擁有者。
1. 刪除以下專案的內容 `<app_root>/pub/static` 目錄，但不包括 `.htaccess` 檔案。 請勿刪除此檔案。
1. 部署靜態檢視檔案： `bin/magento setup:static-content:deploy`

## 開發人員自訂靜態內容部署工具的秘訣

建立靜態內容部署工具的自訂實作時，請只使用使用者端上可用檔案的原子檔案寫入。 如果您使用非原子檔案寫入，這些檔案可能會載入含有部分內容的使用者端。

使其成為原子化的一個選項是寫入儲存在暫存目錄中的檔案，並在寫入結束後複製或移動它們到目的地目錄（從載入到使用者端的目錄）。 如需有關寫入檔案的詳細資訊，請參閱 [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
