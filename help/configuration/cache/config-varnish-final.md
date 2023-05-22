---
title: 最終驗證
description: 確認您的Varnish設定已正確設定為可與Adobe Commerce應用程式搭配使用。
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 清漆組態的最終驗證

現在您已使用 `default.vcl` 由Commerce為您產生，您可以執行一些最終驗證，以確保Varnish正常運作。

## 驗證HTTP回應標頭

使用 `curl` 或其他公用程式，可在您瀏覽網頁瀏覽器中的任何Commerce頁面時檢視HTTP回應標題。

首先，請確定您使用 [開發人員模式](../cli/set-mode.md#change-to-developer-mode)；否則，您將看不到標頭。

例如，

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

重要標題：

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>此值也可以接受： `X-Magento-Cache-Debug: HIT`.

## 檢查頁面載入時間

如果Varnish正常運作，則任何具有可快取區塊的商務頁面應在150毫秒內載入。 此類頁面的範例為前門和店麵類別頁面。

使用瀏覽器檢測器來測量頁面載入時間。

例如，若要使用Chrome檢測器：

1. 存取Chrome中任何可快取的Commerce頁面。
1. 以滑鼠右鍵按一下頁面上的任何位置。
1. 在快顯功能表中，按一下 **[!UICONTROL Inspect Element]**
1. 在檢視窗窗格中，按一下 **[!UICONTROL Network]** 標籤。
1. 重新整理頁面。
1. 捲動至檢視窗窗窗格的頂端，以便檢視所檢視頁面的URL。

   下圖顯示載入 `magento2` 索引頁面。

   ![按一下您正在檢視的頁面](../../assets/configuration/varnish-inspector.png)

   頁面載入時間會顯示在頁面URL旁邊。 在此情況下，載入時間為5毫秒。 這有助於確認Varnish已快取頁面。

1. 若要檢視HTTP回應標題，請按一下頁面URL （在「名稱」欄中）。

   您可以檢視HTTP標頭，驗證HTTP回應標頭一節中會詳細說明這些標頭。

## 驗證商務快取

確定 `<magento_root>/var/page_cache` 目錄是空的：

1. 登入您的Commerce伺服器或切換到檔案系統擁有者。
1. 輸入下列命令：

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. 存取一或多個可快取的Commerce頁面。
1. 檢查 `var/page_cache/` 目錄。

   如果目錄是空的，恭喜您！ 您已成功將Varnish and Commerce設定為搭配使用！

1. 如果您已清除 `var/page_cache/` 目錄，重新啟動Varnish。

>[!TIP]
>
>如果您遇到503 （後端擷取失敗）錯誤，請參閱 [疑難排解503 （服務無法使用）錯誤](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html) 在 _Adobe Commerce說明中心_.
