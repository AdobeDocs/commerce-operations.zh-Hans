---
title: 覆寫組態設定
description: 瞭解如何使用環境變數來覆寫組態設定。
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 0%

---

# 覆寫組態設定

本主題說明如何衍生環境變數名稱來知道設定路徑。 您可以使用環境變數覆寫Adobe Commerce組態設定。 例如，您可以在生產系統上覆寫付款處理者的即時URL的值。

您可以覆寫下列專案的值： _任何_ 使用環境變數進行組態設定；不過，Adobe建議您使用共用組態檔 `config.php`以及系統特定組態檔、 `env.php`，如中所述 [部署一般概覽](../deployment/overview.md).

>[!TIP]
>
>檢視 [設定環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) 中的主題 _雲端基礎結構上的Commerce指南_.

## 環境變數

環境變數名稱包含其範圍，及其特定格式的設定路徑。 以下小節將更詳細地討論如何決定變數名稱。

您可以將變數用於下列任一專案：

- [敏感值](config-reference-sens.md) 必須使用環境變數或 [`magento config:sensitive:set`](../cli/set-configuration-values.md) 命令。
- 系統特定值必須透過以下方式設定：

   - 環境變數
   - 此 [`magento config:set`](../cli/set-configuration-values.md) 命令
   - 管理員後面接著 [`magento app:config:dump` 命令](../cli/export-configuration.md)

可在以下位置找到設定路徑：

- [敏感和系統專屬設定路徑參考](config-reference-sens.md)
- [付款設定路徑參考](config-reference-payment.md)
- [Commerce B2B擴充功能設定路徑參考](config-reference-b2b.md)
- [其他設定路徑參考](config-reference-general.md)

### 變數名稱

系統設定變數名稱的一般格式如下：

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` 可以是：

- 全域範圍(亦即 _全部_ 範圍)

   全域範圍變數的格式如下：

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- 特定範圍（也就是說，設定只會影響指定的商店檢視或網站）

   例如，儲存檢視範圍變數的格式如下：

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   如需有關範圍的詳細資訊，請參閱：

   - [步驟1：尋找網站或商店檢視範圍值](#step-1-find-the-website-or-store-view-scope-value)
   - [有關範圍的Commerce使用手冊主題](https://docs.magento.com/user-guide/configuration/scope.html)
   - [範圍快速參考](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` 是以雙底線字元取代的設定路徑 `/`. 如需詳細資訊，請參閱 [步驟2：設定系統變數](#step-2-set-global-website-or-store-view-variables).

### 變數格式

`<SCOPE>` 分隔自 `<SYSTEM__VARIABLE__NAME>` 加上兩個底線字元。

`<SYSTEM__VARIABLE__NAME>` 衍生自組態設定的 _設定路徑_，亦即 `/` 可唯一識別特定設定的分隔字串。 取代每個 `/` 字元（在設定路徑中具有兩個底線字元）來建立系統變數。

如果設定路徑包含底線字元，底線字元會保留在變數中。

您可以在下列位置找到設定路徑的完整清單：

- [敏感和系統專屬設定路徑參考](config-reference-sens.md)
- [付款設定路徑參考](config-reference-payment.md)
- [Commerce Enterprise B2B擴充功能設定路徑參考](config-reference-b2b.md)
- [其他設定路徑參考](config-reference-general.md)

## 步驟1：尋找網站或商店檢視範圍值

本節探討如何根據下列專案尋找及設定系統組態值： _範圍_ （商店檢視或網站）。 若要設定全域範圍變數，請參閱 [步驟2：設定全域、網站或商店檢視變數](#step-2-set-global-website-or-store-view-variables).

範圍值來自 `store`， `store_group`、和 `store_website` 表格。

- 此 `store` 表格指定存放區檢視名稱和代碼
- 此 `store_website` 表格會指定網站名稱和程式碼

您也可以使用「管理員」來尋找代碼值。

如何讀取表格：

- `Path in Admin` 欄

   逗號前的值是管理員導覽中的路徑。 逗號後的值是右窗格中的選項。

- `Variable name` 欄是對應環境變數的名稱。

   您可以視需要將這些組態引數的系統值指定為環境變數。

   - 整個變數名稱一律為全大寫
   - 變數名稱的開頭為 `CONFIG__` （注意兩個底線字元）
   - 您可以找到 `<STORE_VIEW_CODE>` 或 `<WEBSITE_CODE>` Admin或Commerce資料庫中變數名稱的一部分，如下列小節所示。
   - 您可以找到 `<SYSTEM__VARIABLE__NAME>` 如中所述 [步驟2：設定全域、網站或商店檢視變數](#step-2-set-global-website-or-store-view-variables).

### 在管理員中尋找網站或商店檢視範圍

下表概述如何在「管理員」中尋找網站或儲存檢視值。

| 說明 | 管理員中的路徑 | 變數名稱 |
|--------------|--------------|----------------------|
| 建立、編輯、刪除商店檢視 | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| 建立、編輯、刪除網站 | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

例如，若要在「管理員」中尋找網站或儲存檢視範圍值：

1. 以獲授權檢視網站的使用者身分登入管理員。
1. 按一下 **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. 按一下網站或商店檢視的名稱。

   右窗格顯示如下。

   ![尋找網站程式碼](../../assets/configuration/website-code.png)

1. 範圍名稱會顯示在 **[!UICONTROL Code]** 欄位。
1. 繼續使用 [步驟2：設定全域、網站或商店檢視變數](#step-2-set-global-website-or-store-view-variables).

### 在資料庫中尋找網站或存放區檢視範圍

若要從資料庫取得這些值：

1. 如果您尚未以檔案系統擁有者的身分登入您的開發系統，請先登入。
1. 輸入下列命令：

   ```bash
   mysql -u <database-username> -p
   ```

1. 在 `mysql>` 提示，請依照顯示的順序輸入以下命令：

   ```shell
   use <database-name>;
   ```

1. 使用下列SQL查詢來尋找相關值：

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   範例如下：

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. 使用以下專案的值： `code` 欄做為範圍名稱，而不是 `name` 值。

   例如，若要設定測試網站的設定變數，請使用下列格式：

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   位置 `<SYSTEM__VARIABLE__NAME>` 來自下一節。

## 步驟2：設定全域、網站或商店檢視變數

本節將討論如何設定系統變數。

- 若要設定全域範圍（即所有網站、商店和商店檢視）的值，請在變數名稱開頭使用 `CONFIG__DEFAULT__`.

- 若要為特定商店檢視或網站設定值，請依照中所述啟動變數名稱 [步驟1：尋找範圍值](#step-1-find-the-website-or-store-view-scope-value)：

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- 變數名稱的最後一部分是設定路徑，每個設定都是唯一的。

[檢視一些範例](#examples).

下表顯示一些範例變數。

| 說明 | 管理中的路徑（省略） **商店** > **設定** > **設定**) | 變數名稱 |
|--------------|--------------|----------------------|
| Elasticsearch伺服器主機名稱 | 目錄> **目錄**， **Elasticsearch伺服器主機名稱** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch伺服器連線埠 | 目錄> **目錄**， **Elasticsearch伺服器連線埠** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| 出貨國家/地區來源 | 銷售> **送貨設定** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| 自訂管理員URL | 進階> **管理員** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| 自訂管理路徑 | 進階> **管理員** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## 範例

本節說明如何尋找某些範例變數的值。

### Elasticsearch伺服器主機名稱

若要尋找全域HTML縮制的變數名稱：

1. 決定範圍。

   這是全域範圍，所以變數名稱開頭為 `CONFIG__DEFAULT__`

1. 變數名稱的其餘部分為 `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **結果**：變數名稱為 `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### 出貨國家/地區來源

若要尋找出貨國家/地區的變數名稱，請執行下列步驟：

1. 決定範圍。

   在中尋找範圍 [資料庫](#find-a-website-or-store-view-scope-in-the-database) 如步驟1中所述：尋找網站或商店檢視範圍值。 (您也可以在「管理員」中找到值，如下所示 [步驟2中的表格：設定全域、網站或商店檢視變數](#step-2-set-global-website-or-store-view-variables。

   例如，範圍可以是 `CONFIG__WEBSITES__DEFAULT`.

1. 變數名稱的其餘部分為 `SHIPPING__ORIGIN__COUNTRY_ID`.

   **結果**：變數名稱為 `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## 如何使用環境變數

使用PHP的設定組態值為變數 [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) 關聯陣列。 您可以在Commerce執行時執行的任何PHP指令碼中設定值。

>[!TIP]
>
>設定變數值 `index.php` 或 `pub/index.php` 並非總是如預期般運作，因為根據Web伺服器組態，可能會使用不同的應用程式進入點。 透過放置 `$_ENV` 中的指令 `app/bootstrap.php` 檔案，無論不同的應用程式入口點為何， `$_ENV` 指示詞一律執行，因為 `app/bootstrap.php` 檔案會在Commerce架構中載入。

設定兩個的範例 `$_ENV` 值如下：

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

逐步範例顯示於 [使用環境變數設定設定設定值](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- 若要使用您在 `$_ENV` 陣列，您必須設定 `variables_order = "EGPCS"`（環境、取得、發佈、Cookie和伺服器） `php.ini` 檔案。 如需詳細資訊，請參閱 [PHP檔案](https://www.php.net/manual/en/ini.core.php).
>
>- 對於雲端基礎結構上的Adobe Commerce，如果您嘗試使用 [Project Web介面](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)，您必須在變數名稱前面加上 `env:`. 例如：
>
>![環境變數範例](../../assets/configuration/cloud-console-envvariable.png)
