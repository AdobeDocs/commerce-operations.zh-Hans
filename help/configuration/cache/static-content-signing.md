---
title: 靜態內容快取
description: 瞭解靜態內容簽署以及如何啟用或停用此功能。
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# 靜態內容快取

為改善效能，Commerce將 `Expires` 靜態資源的標頭，例如影像、JavaScript和CSS檔案。
設定 `Expires` 靜態資源上的標頭會告訴瀏覽器快取該URL上的資源，並提供快取版本直到它過期為止。
這是常見的 [最佳實務](https://developer.yahoo.com/performance/rules.html#expires=) 用於快取靜態資源。

當瀏覽器快取靜態資源，而該資源在伺服器上變更時，您必須清除瀏覽器快取，才能下載新版本。
如果您是網站管理員，手動清除瀏覽器快取可正常運作，但當您想要讓使用者下載靜態資源的新版本時，這不是對使用者提出的適當請求。

## 靜態內容簽署

靜態內容簽署是Commerce功能，可讓您讓靜態資源的瀏覽器快取失效。
Commerce會將部署版本新增至靜態檔案的URL，以達成此目的。

以下是使用版本簽署的URL範例：

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

當您執行命令時 [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) 若要部署靜態內容，Commerce會自動變更部署版本。
這會變更靜態檔案的URL，並強制瀏覽器載入檔案的新版本。

Commerce預設會啟用此功能，Adobe建議啟用此功能，以防止瀏覽器提供舊靜態資源時出現問題。

您可以在下列位置找到此功能的設定： [**[!UICONTROL Stores]**>設定>設定>**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![靜態檔案設定](../../assets/configuration/static-files-settings.png)

判斷狀態：

```bash
bin/magento config:show dev/static/sign
```

啟用或停用靜態內容簽署：

```bash
bin/magento config:set dev/static/sign <value>
```

位置 `<value>` 為1 （已啟用）或0 （已停用）。

## 版本簽章

Commerce會將版本簽章直接附加為靜態檢視檔案的基礎URL之後的路徑元件，以保留靜態資源中相對URL的完整性。
這也會強制瀏覽器將相對URL解析為正確的已簽署來源，同時保持其內容與簽名值的存在/不存在無關。

當瀏覽器向伺服器請求已簽署的來源時，伺服器會使用URL重寫來從URL中移除簽名元件。

## 部署期間的使用情況

升級或修改靜態資源後，您必須執行 `setup:static-content:deploy` 部署版本和更新靜態內容的命令，會強制瀏覽器載入更新的資源。

如果您將程式碼部署在單獨的伺服器上，並使用程式碼存放庫將其移至生產環境以減少停機時間，您也必須新增檔案 `pub/static/deployed_version.txt` 至存放庫。
此檔案包含已部署靜態內容的新版本。
