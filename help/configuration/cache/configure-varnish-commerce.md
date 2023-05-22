---
title: 設定Commerce專用清漆
description: 瞭解如何更新和管理Commerce應用程式的Varnish設定檔案。
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 設定Commerce應用程式以使用Varnish

若要設定Commerce使用清漆：

1. 以管理員身分登入管理員。
1. 按一下 **[!UICONTROL Stores]** >設定> **設定** > **進階** > **系統** > **完整頁面快取**.
1. 從 **[!UICONTROL Caching Application]** 清單，按一下 **清漆快取**.
1. 在 **[!UICONTROL TTL for public content]** 欄位。
1. 展開 **[!UICONTROL Varnish Configuration]** 並輸入下列資訊：

   | 欄位 | 說明 |
   | ----- | ----------- |
   | 存取清單 | 輸入完整的主機名稱、IP位址，或 [無類別網域間路由(CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) 表示法IP位址範圍，用於讓內容失效。 另請參閱 [清漆快取清除](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | 後端主機 | 輸入完整的主機名稱或IP位址，並接聽清漆的連線埠 _後端_ 或 _原始伺服器_；也就是說，提供內容清漆的伺服器會加速。 通常這是您的Web伺服器。 另請參閱 [清漆快取後端伺服器](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | 後端連線埠 | 原始伺服器的接聽連線埠。 |
   | 寬限期 | 寬限期會決定Varnish在後端無回應時提供過時內容的時間長度。 預設值為300秒。 |

1. 按一下 **儲存設定**.

您也可以使用C命令列介面工具，從命令列啟動Varnish （而不是登入Admin）：

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## 匯出Varnish組態檔

若要從Admin匯出Varnish設定檔：

1. 按一下其中一個匯出按鈕以建立 `varnish.vcl` 您可以搭配Varnish使用。

   例如，如果您有Varnish 4，請按一下 **匯出清漆4的VCL**

   下圖顯示一個範例：

   ![設定Commerce以在管理員中使用塗漆](../../assets/configuration/varnish-admin-22.png)

1. 備份您現有的 `default.vcl`. 然後重新命名 `varnish.vcl` 您剛剛匯出的檔案 `default.vcl`. 然後將檔案複製到 `/etc/varnish/` 目錄。

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe建議您開啟 `default.vcl` 並變更以下專案的值： `acl purge` 到Varnish主機的IP位址。 （您可以在不同的行上指定多個主機，也可以使用CIDR標籤法。）

   例如，

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. 如果您想自訂Vagrant健康情況檢查或寬限模式或saint模式設定，請參閱 [進階清漆設定](config-varnish-advanced.md).

1. 重新啟動Varnish和您的網頁伺服器：

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 快取靜態檔案

預設不應快取靜態檔案，但如果您想要快取它們，可以編輯區段 `Static files caching` 在VCL中有以下內容：

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

您必須進行這些變更，才能設定Commerce使用Varnish。
