---
title: 進階清漆設定
description: 設定進階Varnish功能，包括健康狀態檢查、寬限和聖人模式。
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 0%

---

# 進階清漆設定

Varnish提供數項功能，可防止客戶在Commerce伺服器無法正常運作時遭遇長時間延遲和逾時。 這些功能可在以下位置設定： `default.vcl` 檔案。 本主題說明Commerce在您從Admin下載的VCL （清漆組態語言）檔案中提供的新增功能。

請參閱 [清漆參考手冊](https://varnish-cache.org/docs/6.3/reference/index.html) 以取得有關使用清漆組態語言的詳細資訊。

## 健康情況檢查

Varnish健康情況檢查功能會輪詢Commerce伺服器，判斷伺服器是否及時回應。 如果正常回應，新內容會在存留時間(TTL)期間過期後重新產生。 否則，Varnish一律會提供過時的內容。

Commerce會定義下列預設健康情況檢查：

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

此健康情況檢查每5秒會呼叫 `pub/health_check.php` 指令碼。 此指令碼會檢查伺服器、每個資料庫和Redis （如果已安裝）的可用性。 指令碼必須在2秒內傳回回應。 如果指令碼判斷這些資源中有任何資源停用，則會傳回500 HTTP錯誤代碼。 如果在10次嘗試中，有6次收到此錯誤代碼，則會將後端視為不健康。

此 `health_check.php` 指令碼位於 `pub` 目錄。 如果您的Commerce根目錄為 `pub`，然後請務必在 `url` 引數來源 `/pub/health_check.php` 至 `health_check.php`.

如需詳細資訊，請參閱 [清漆健康情況檢查](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) 說明檔案。

## 寬限模式

寬限模式可讓Varnish將快取中的物件保持在超過其TTL值的位置。 然後，清漆可在擷取新版本時提供過期（過時）的內容。 這能改善流量並縮短載入時間。 它用於以下情況：

- 當Commerce後端狀況良好，但請求所花的時間比正常情況長
- 當Commerce後端不正常時。

此 `vcl_hit` 副程式會定義Varnish如何回應已快取之物件的要求。

### 當Commerce後端正常時

健康情況檢查確定Commerce後端健康時，Varnish會檢查時間是否仍在寬限期內。 預設寬限期為300秒，但商家可以從管理員設定值，如所述 [設定Commerce使用清漆](configure-varnish-commerce.md). 如果寬限期尚未過期，Varnish會傳送過時內容，並從Commerce伺服器非同步重新整理物件。 如果寬限期已過，Varnish會提供過時內容，並從Commerce後端同步重新整理物件。

Varnish提供過時物件的時間長度上限是寬限期（預設為300秒）和TTL值(預設為86400秒)的總和。

若要從變更預設寬限期 `default.vcl` 檔案，編輯 `vcl_hit` 副程式：

```conf
if (obj.ttl + 300s > 0s) {
```

### 當Commerce後端不正常時

如果Commerce後端無回應，Varnish會從快取中提供三天過時的內容（或如中的定義） `beresp.grace`)加上剩餘TTL （預設為一天），除非手動清除快取內容。

## Saint模式

Saint模式會在可設定的時間內排除不健康的後端。 因此，當使用Varnish作為負載平衡器時，不健康的後端無法提供流量。 Saint模式可與寬限模式搭配使用，以允許複雜處理不健全的後端伺服器。 例如，如果一個後端伺服器狀況不良，重試可以路由到另一個伺服器。 如果所有其他伺服器都停止運作，則提供過時的快取物件。 saint模式後端主機和中斷期間定義於 `default.vcl` 檔案。

Saint模式也可以用於商務執行個體個別離線以執行維護和升級任務，而不會影響Commerce網站的可用性。

### Saint模式先決條件

指定一個電腦作為主要安裝。 在此電腦上安裝Commerce、mySQL資料庫和Varnish的主要執行個體。

在所有其他電腦上，Commerce執行個體必須能夠存取主要電腦的mySQL資料庫。 次要電腦也應具有主要商務執行個體檔案的存取權。

或者，可以在所有機器上關閉靜態檔案版本設定。 您可從「 Admin 」底下的「 」存取此專案 **商店** >設定> **設定** > **進階** > **開發人員** > **靜態檔案設定** > **簽署靜態檔案** = **否**.

最後，所有Commerce執行個體都必須處於生產模式。 在Varnish開始之前，清除每個執行個體上的快取。 在Admin中，前往 **系統** >工具> **快取管理** 並按一下 **排清Magento快取**. 您也可以執行下列命令來清除快取：

```bash
bin/magento cache:flush
```

### 安裝

Saint模式不是主要Varnish套件的一部分。 它是獨立版本設定 `vmod` 必須下載並安裝該軟體。 因此，您應該從來源重新編譯Varnish，如下列文章所述：

- [安裝Varnish 6.4](https://varnish-cache.org/docs/6.4/installation/install.html)
- [安裝Varnish 6.0](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

重新編譯之後，您可以安裝Saint模式模組。 一般而言，請遵循下列步驟：

1. 從取得原始程式碼 [塗漆模組](https://github.com/varnish/varnish-modules). 複製Git版本（主要版本），因為0.9.x版本包含原始程式碼錯誤。
1. 使用autotools建置原始程式碼：

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

另請參閱 [清漆模組集合](https://github.com/varnish/varnish-modules) 瞭解安裝Saint模式模組的相關資訊。

### 範例VCL檔案

下列程式碼範例顯示必須新增至VCL檔案才能啟用saint模式的程式碼。 放置 `import` 陳述式和 `backend` 檔案頂端的定義。

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
