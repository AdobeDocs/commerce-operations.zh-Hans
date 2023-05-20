---
title: 啟用或停用維護模式
description: 請依照下列步驟，自訂當您的Adobe Commerce或Magento Open Source部署因維護而停止時，客戶會看到的內容。
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# 啟用或停用維護模式

下列指南參考標準維護模式頁面。 如果您需要使用自訂維護頁面，請參閱 [建立自訂維護頁面](../../upgrade/troubleshooting/maintenance-mode-options.md) 主題。

Adobe Commerce和Magento Open Source使用 [維護模式](../../configuration/bootstrap/application-modes.md#maintenance-mode) 以停用啟動程式。 在維護、升級或重新設定網站時，停用啟動載入功能會很有幫助。

應用程式會偵測維護模式，如下所示：

* 若 `var/.maintenance.flag` 不存在，維護模式為關閉且應用程式正常運作。
* 否則，維護模式會開啟，除非 `var/.maintenance.ip` 已存在。

   `var/.maintenance.ip` 可以包含IP位址清單。 如果使用HTTP存取進入點，且使用者端IP位址對應至該清單中的其中一個專案，則維護模式會關閉。

## 安裝應用程式

使用此命令來啟用或停用維護模式之前，您必須 [安裝應用程式](../advanced.md).

## 啟用或停用維護模式

使用 `magento maintenance` 啟用或停用維護模式的CLI命令。

命令使用方式：

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

此 `--ip=<ip address>` 選項是劐免於維護模式的IP位址（例如，進行維護的開發人員）。 若要在同一命令中免除多個IP位址，請多次使用選項。

>[!NOTE]
>
>使用 `--ip=<ip address>` 替換為 `magento maintenance:disable` 儲存IP清單以供稍後使用。 若要清除劐免IP清單，請使用 `magento maintenance:enable --ip=none` 或參閱 [維護劐免IP位址清單](#maintain-the-list-of-exempt-ip-addresses).

此 `bin/magento maintenance:status` 命令會顯示維護模式的狀態。

例如，啟用沒有IP位址劐免的維護模式：

```bash
bin/magento maintenance:enable
```

若要為192.0.2.10和192.0.2.11以外的所有使用者端啟用維護模式：

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

將應用程式置於維護模式後，您必須停止所有訊息佇列消費者程式。
尋找這些處理程式的一種方式是執行 `ps -ef | grep queue:consumers:start` 命令，然後執行 `kill <process_id>` 每個消費者的命令。 在多節點環境中，請在每個節點上重複此工作。

## 維護劐免IP位址清單

若要維護劐免IP位址清單，您可以使用 `[--ip=<ip list>]` 選項，或者您可以使用下列選項：

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

此 `<ip address> .. <ip address>` 語法是選用的空格分隔清單，列出要劐免的IP位址。

此 `--none` 選項會清除清單。

## 多商店設定

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

如果您想要設定多個商店，每個商店都有不同的版面和當地語系化內容，請傳遞 `$_GET['skin']` 指定處理器的引數。

在以下範例中，我們使用 `503` 輸入錯誤範本檔案，這需要當地語系化的內容。

的建構函式 `Error_Processor` 類別接受 `skin` GET引數以變更版面：

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

這也可以新增到中的重寫規則 `.htaccess` 附加檔案的 `skin` URL的引數。

### $_GET[&#39;外觀&#39;] 引數

若要使用 `skin` 引數：

1. 檢查 `.maintenance.flag` 已存在。
1. 記下主機位址，該位址指 `HTTP_HOST`或任何其他變數（例如ENV變數）。
1. 檢查 `skin` 引數存在。
1. 使用以下重寫規則設定引數。

   以下是重寫規則的一些範例：

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * 重寫規則 `^ %{REQUEST_URI}?skin=sub` [L]

1. 複製下列檔案：

   * `pub/errors/default/503.phtml` 至 `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` 至 `pub/errors/sub/styles.css`

1. 編輯這些檔案，以在 `503.phtml` 中的檔案和自訂樣式 `styles.css` 檔案。

   確保您的路徑指向 `errors` 目錄。 目錄名稱必須符合URL引數，如 `RewriteRule`. 在上一個範例中， `sub` 使用directory，它在 `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>此 [nginx](../../configuration/multi-sites/ms-nginx.md) 必須為多存放區設定新增設定。
