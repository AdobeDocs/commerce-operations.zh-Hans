---
title: 設定網頁伺服器
description: 瞭解如何設定網頁伺服器以使用Varnish。
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# 設定網頁伺服器

將網頁伺服器設定成在預設連線埠80以外的連線埠上接聽，因為Varnish會直接回應傳入的HTTP要求，而不是網頁伺服器。

以下各節以連線埠8080為例。

**變更Apache 2.4接聽連線埠**：

1. 開啟 `/etc/httpd/conf/httpd.conf` 在文字編輯器中。
1. 找到 `Listen` 指令。
1. 將監聽連線埠的值變更為 `8080`. （您可以使用任何可用的接聽連線埠。）
1. 將變更儲存至 `httpd.conf` 並退出文字編輯器。

## 修改Varnish系統設定

若要修改Varnish系統組態：

1. 作為使用者，具有 `root` 許可權，在文字編輯器中開啟您的「消失」設定檔案：

   - CentOS 6： `/etc/sysconfig/varnish`
   - CentOS 7： `/etc/varnish/varnish.params`
   - Debian： `/etc/default/varnish`
   - Ubuntu： `/etc/default/varnish`

1. 將Varnish接聽連線埠設定為80：

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   對於Varnish 4.x，請確定DAEMON_OPTS包含正確的監聽連線埠 `-a` 引數（即使VARNISH_LISTEN_PORT設定為正確的值）：

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. 將變更儲存至Varnish設定檔案並退出文字編輯器。

### 修改預設VCL

本節討論如何提供最低設定，讓Varnish傳回HTTP回應標題。 這可讓您在設定 [!DNL Commerce] 使用Varnish的應用程式。

若要將清漆設定為最少：

1. 備份 `default.vcl`：

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 開啟 `/etc/varnish/default.vcl` 在文字編輯器中。
1. 找到下列區段：

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. 取代的值 `.host` 具有完整的主機名稱或IP位址，以及Varnish的接聽連線埠 _後端_ 或 _原始伺服器_；也就是說，提供內容Varnish的伺服器將會加速。

   通常這是您的Web伺服器。 另請參閱 [後端伺服器](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) 在 _清漆指南_.

1. 取代的值 `.port` 網頁伺服器的監聽連線埠（此範例中為8080）。

   範例： Apache安裝在主機192.0.2.55上，而Apache正在連線埠8080上接聽：

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >如果Varnish和Apache在相同主機上執行，Adobe建議您使用IP位址或主機名稱，而不要使用 `localhost`.

1. 將變更儲存至 `default.vcl` 並退出文字編輯器。

1. 重新啟動清漆：

   ```bash
   service varnish restart
   ```

如果Varnish無法啟動，請嘗試從命令列執行，如下所示：

```bash
varnishd -d -f /etc/varnish/default.vcl
```

這應該會顯示錯誤訊息。


>[!INFO]
>
>如果Varnish不是以服務啟動，您必須設定SELinux規則以允許其執行。

## 驗證清漆是否正常運作

以下小節討論如何驗證Varnish是否正常運作，但是 _不含_ 設定Commerce以使用它。 在設定Commerce之前，請先嘗試此做法。

依照顯示的順序，執行下列各節中討論的工作：

- [開始塗漆](#start-varnish)
- [&#39;netstat&#39;](#netstat)

### 開始塗漆

輸入： `service varnish start`

如果Varnish無法作為服務啟動，請從命令列啟動，如下所示：

1. 啟動Varnish CLI：

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. 啟動Varnish子程式：

   出現提示時，輸入 `start`

   系統會顯示下列訊息，確認啟動成功：

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

登入Varnish伺服器並輸入下列命令：

```bash
netstat -tulpn
```

請特別尋找以下輸出：

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

前文顯示了在連線埠80上執行的Varnish和在連線埠8080上執行的Apache。

如果您沒有看到輸出 `varnishd`，確認Varnish正在執行。

另請參閱 [`netstat` 選項](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## 安裝Commerce軟

安裝Commerce軟體（如果尚未安裝）。 提示輸入基本URL時，請使用Varnish主機和連線埠80 （針對Varnish），因為Varnish會接收所有傳入的HTTP請求。

安裝Commerce時可能發生錯誤：

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

如果您遇到此錯誤，請編輯 `default.vcl` 並將逾時新增至 `backend` 區段如下：

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## 驗證HTTP回應標頭

現在，您可以檢視從任何頁面傳回的HTML回應標題，以確認Varnish正在為頁面提供服務。

檢視標題之前，您必須先為開發人員模式設定Commerce 。 有幾種方法可以做到，最簡單的方法就是進行修改 `.htaccess` 商務應用程式根目錄中的。 您也可以使用 [`magento deploy:mode:set`](../cli/set-mode.md) 命令。

### 為開發人員模式設定Commerce

若要針對開發人員模式設定Commerce，請使用 [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) 命令。

### 檢視清漆記錄

請確定Varnish正在執行，然後在Varnish伺服器上輸入下列命令：

```bash
varnishlog
```

在網頁瀏覽器中，前往任何Commerce頁面。

命令提示字元視窗中會顯示一長串回應標頭。 尋找類似以下內容的標頭：

```terminal
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

如果這類標題有 _not_ 顯示，停止塗漆，檢查您的 `default.vcl`，然後重試。

### 檢視HTML回應標頭

有數種方式可檢視回應標題，包括使用瀏覽器外掛程式或瀏覽器檢測器。

以下範例使用 `curl`. 您可以從任何可以使用HTTP存取Commerce伺服器的電腦輸入此命令。

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

例如，

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

尋找類似以下內容的標頭：

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
