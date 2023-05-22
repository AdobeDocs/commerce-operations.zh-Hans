---
title: 應用程式初始化和啟動程式
description: 閱讀Commerce應用程式的初始化和啟動程式邏輯。
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# 初始化和啟動程式概述

若要執行Commerce應用程式，下列動作會實作於 [pub/index.php][index]：

- 包含 [app/bootstrap.php][bootinitial]，會執行必要的初始化常式，例如錯誤處理、初始化自動載入器、設定設定檔選項，以及設定預設時區。
- 建立例項 [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- 建立Commerce應用程式例項： [\Magento\Framework\AppInterface][app-face]
- 執行商務

## Bootstrap執行邏輯

[啟動程式物件][bootinitial] 會使用以下演演算法來執行Commerce應用程式：

1. 初始化錯誤處理常式。
1. 建立 [物件管理員][object] 以及基本共用服務，適用於任何地方，並受環境影響。 環境引數會適當地插入這些物件中。
1. 判斷維護模式為 _not_ 已啟用；否則，會終止。
1. 判斷是否已安裝Commerce應用程式；否則，會終止。
1. 啟動商務應用程式。

   應用程式啟動期間任何未攔截到的例外狀況，都會自動傳回 `catchException()` 可用來處理例外狀況的方法。 後者必須傳回 `true` 或 `false`：

   - 若 `true`：商務已成功處理例外狀況。 無需執行任何其他操作。
   - 若 `false`：（或任何其他空白結果） Commerce未處理例外狀況。 Bootstrap物件會執行預設的例外狀況處理子常式。

1. 傳送應用程式物件提供的回應。

   >[!INFO]
   >
   >聲稱已安裝Commerce應用程式且未處於維護模式，是 `\Magento\Framework\App\Bootstrap` 類別。 建立啟動程式物件時，您可以使用入口點指令碼來修改它。

   修改啟動程式物件的範例進入點指令碼：

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## 預設例外狀況處理

bootstrap物件會指定Commerce應用程式如何處理未攔截到的例外狀況，如下所示：

- 在 [開發人員模式](../bootstrap/application-modes.md#developer-mode)，會依原樣顯示例外狀況。
- 在任何其他模式中，會嘗試記錄例外狀況並顯示一般錯誤訊息。
- 使用錯誤碼終止商務 `1`

## 進入點應用程式

我們有以下入口點應用程式（即Commerce定義的應用程式，由Web伺服器用作目錄索引）：

### HTTP進入點

[\Magento\Framework\App\Http][http] 的運作方式如下：

1. 決定 [應用程式區域](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. 啟動前端控制器和路由系統，以尋找並執行控制器動作。
1. 使用HTTP回應物件來傳回從控制器動作取得的結果。
1. 錯誤處理（按照以下優先順序）：

   1. 如果您使用 [開發人員模式](../bootstrap/application-modes.md#developer-mode)：
      - 如果未安裝Commerce應用程式，請重新導向至安裝精靈。
      - 如果已安裝Commerce應用程式，則顯示錯誤和HTTP狀態碼500 （內部伺服器錯誤）。
   1. 如果Commerce應用程式處於維護模式，會顯示使用者易記的「服務無法使用」登陸頁面，HTTP狀態碼為503 （服務無法使用）。
   1. 如果商務應用程式為 _not_ 已安裝，重新導向至安裝精靈。
   1. 如果工作階段無效，請重新導向至首頁。
   1. 如果有任何其他應用程式初始化錯誤，顯示使用者易記的「找不到頁面」頁面，其中HTTP狀態碼為404 （找不到）。
   1. 發生任何其他錯誤時，顯示包含HTTP回應503且方便使用的「服務無法使用」頁面，並產生錯誤報告及在頁面上顯示其ID。

### 靜態資源進入點

[\Magento\Framework\App\StaticResource][static-resource] 是用於擷取靜態資源（例如CSS、JavaScript和影像）的應用程式。 它會延遲對靜態資源執行任何動作，直到請求該資源為止。

>[!INFO]
>
>靜態檢視檔案的進入點未用於 [生產模式](application-modes.md#production-mode) 以避免在伺服器上發生潛在利用漏洞的情形。 在生產模式中，Commerce應用程式預期所有必要資源都存在於 `<your Commerce install dir>/pub/static` 目錄。

在預設或開發人員模式中，會根據適當的所指定的重寫規則，將不存在的靜態資源的請求重新導向至靜態進入點 `.htaccess`.
當請求被重新導向到進入點時，商務應用程式會根據擷取的引數剖析請求的URL並尋找請求的資源。

- 在 [開發人員](application-modes.md#developer-mode) 模式，則會傳回檔案的內容，以便每次請求資源時，傳回的內容都是最新的。
- 在 [預設](application-modes.md#default-mode) 模式，則會發佈擷取的資源，以便先前請求的URL可存取該資源。

   伺服器會以處理靜態檔案的方式來處理靜態資源的所有未來請求；也就是說，不會涉及進入點。 如果需要將已發佈的檔案與原始檔案同步， `pub/static` 應該移除目錄；因此，檔案會在下次請求時自動重新發佈。

### 媒體資源進入點

[Magento\MediaStorage\App\Media][media] 從資料庫擷取媒體資源（亦即任何上傳至媒體儲存空間的檔案）。 每當資料庫設定為媒體儲存體時，就會使用它。

`\Magento\Core\App\Media` 嘗試在設定的資料庫儲存空間中尋找媒體檔案，並將其寫入 `pub/static` 目錄，然後傳回其內容。 發生錯誤時，它會在沒有內容的標頭中傳回HTTP 404 （找不到）狀態代碼。

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
