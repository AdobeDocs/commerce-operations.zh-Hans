---
title: 管理快取
description: 管理快取型別和檢視快取狀態。
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# 管理快取

{{file-system-owner}}

## 快取型別

Commerce 2具有以下快取型別：

| 快取型別「易記」名稱 | 快取型別代碼名稱 | 說明 |
|--- |--- |--- |
| 設定 | 設定 | Commerce會從所有模組收集設定、合併設定，並將合併的結果儲存至快取。 此快取也包含儲存在檔案系統和資料庫中的儲存區特定設定。 修改組態檔後，請清除或清除此快取型別。 |
| 版面 | 版面 | 編譯的頁面配置（也就是來自所有元件的配置元件）。 修改版面配置檔案後，清除或清除此快取型別。 |
| 封鎖HTML輸出 | block_html | 每個區塊的頁面片段HTML。 修改檢視圖層後，請清除或排清此快取型別。 |
| 集合資料 | 集合 | 資料庫查詢的結果。 如有必要，Commerce會自動清理此快取，但第三方開發人員可以將任何資料放入快取的任何區段中。 如果您的自訂模組使用的邏輯導致Commerce無法清除的快取專案，請清除或清除此快取型別。 |
| DDL | db_ddl | 資料庫結構描述。 如有必要，Commerce會自動清理此快取，但第三方開發人員可以將任何資料放入快取的任何區段中。 在對資料庫結構描述進行自訂變更後，清除或清除此快取型別。 （換言之，此更新不屬於Commerce本身。） 自動更新資料庫架構的一種方法是使用 `magento setup:db-schema:upgrade` 命令。 |
| 編譯的設定 | compiled_config | 編譯設定 |
| 實體屬性值(EAV) | eav | 與EAV屬性相關的中繼資料（例如，儲存標籤、相關PHP程式碼的連結、屬性呈現、搜尋設定等）。 您通常不需要清除或排清此快取型別。 |
| 頁面快取 | full_page | 產生的HTML頁面。 如有必要，Commerce會自動清理此快取，但第三方開發人員可以將任何資料放入快取的任何區段中。 修改影響HTML輸出的程式碼層級後，清除或排清此快取型別。 建議啟用此快取，因為快取HTML可大幅改善效能。 |
| 反射 | 反射 | 移除Webapi模組與客戶模組之間的相依性。 |
| 翻譯 | 轉換 | 合併來自所有模組的翻譯後，合併快取將會被清除。 |
| 整合設定 | config_integration | 編譯的整合。 變更或新增整合後，請清除或清除此快取。 |
| 整合API設定 | config_integration_api | 商店整合的編譯整合API設定。 |
| Web服務設定 | config_webservice | 快取Web API結構。 |
| 客戶通知 | customer_notification | 顯示在使用者介面中的臨時通知。 |

## 檢視快取狀態

若要檢視快取的狀態，請輸入

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

範例如下：

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

## 啟用或停用快取型別

這個命令可讓您啟用或停用所有快取型別，或僅停用您指定的快取型別。 在開發期間，停用快取型別很有用，因為您不必清除快取即可看到變更的結果；但是，停用快取型別會對效能造成不良影響。

>[!INFO]
>
>從2.2版開始，您在生產模式下執行Commerce時，只能使用命令列啟用或停用快取型別。 如果在開發人員模式下執行Commerce，您可以使用命令列或手動啟用或停用快取型別。 在執行此操作之前，您必須手動進行 `<magento_root>/app/etc/env.php` 可由 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).

您可以清除(也稱為 _排清_ 或 _重新整理_)快取型別。

命令選項：

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

省略 `[type]` 同時啟用或停用所有快取型別。 此 `type` option是以空格分隔的快取型別清單。

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

若要列出快取型別及其狀態：

```bash
bin/magento cache:status
```

例如，若要停用完整頁面快取和DDL快取：

```bash
bin/magento cache:disable db_ddl full_page
```

範例結果：

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>啟用快取型別會自動清除該快取型別。

>[!INFO]
>
>自2.3.4版起，Commerce會在擷取所有系統EAV屬性時加以快取。 以此方式快取EAV屬性可改善效能，因為它會減少對DB的插入/選取要求數量。 不過，它也會增加快取網路大小。 開發人員可藉由執行 `bin/magento config:set dev/caching/cache_user_defined_attributes 1` 命令。 這也可以從管理員完成，當在 [開發人員模式](../bootstrap/application-modes.md) 透過設定 **商店** >設定 **設定** > **進階** > **開發人員** > **快取設定** > **快取使用者定義的屬性** 至 **是**.

## 清除和排清快取型別

若要從快取中永久刪除過期的專案，您可以 _clean_ 或 _排清_ 快取型別：

- 清除快取型別只會從已啟用的Commerce快取型別中刪除所有專案。 換言之，此選項不會影響其他程式或應用程式，因為它只會清除Commerce使用的快取。

   停用的快取型別不會清除。

   >[!TIP]
   >
   >升級Magento Open Source或Adobe Commerce版本、從Magento Open Source升級至Adobe Commerce，或安裝Adobe Commerce或任何模組適用的B2B後，請務必清理快取。

- 清除快取型別會清除快取儲存體，這可能會影響使用相同儲存體的其他程式應用程式。

如果您已嘗試清除快取，但仍有無法隔離的問題，請清除快取型別。

命令使用方式：

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

位置 `[type]` 是以空格分隔的快取型別清單。 省略 `[type]` 同時清除或排清所有快取型別。 例如，若要排清所有快取型別，請輸入

```bash
   bin/magento cache:flush
```

範例結果：

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   config_webservice
   translate
```

>[!TIP]
>
>您也可以在Admin中清理和排清快取型別。 前往 **系統** > **工具** > **快取管理**. **排清快取儲存體** 相當於 `bin/magento cache:flush`. **排清Magento快取** 相當於 `bin/magento cache:clean`.
