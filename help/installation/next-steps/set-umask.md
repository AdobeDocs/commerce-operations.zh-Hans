---
title: 設定umask （選擇性）
description: 透過限制檔案系統許可權，改善Adobe Commerce或Magento Open Source內部部署安裝的安全性狀態。
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 設定umask （選擇性）

網頁伺服器群組必須具有檔案系統中特定目錄的寫入許可權；不過，您可能想要更嚴格的安全性，尤其是在生產環境中。 我們為您提供靈活性，讓您使用 [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

我們的解決方案是讓您可選擇建立名為的檔案 `magento_umask` 限制網站伺服器群組和其他人的許可權的應用程式根目錄中。

>[!NOTE]
>
>我們建議僅在一位使用者或共用託管系統上變更主任務。 如果您有私人應用程式伺服器，群組必須擁有檔案系統的寫入許可權；umask會移除群組的寫入許可權。

預設的umask (不含 `magento_umask` 已指定)為 `002`，這表示：

* 775 for directories，表示使用者可完全控制、群組可完全控制，並允許所有人周遊目錄。 共用託管提供者通常需要這些許可權。

* 664適用於檔案，這表示使用者可寫入、群組可寫入，且其他所有人皆為唯讀

一個常見建議是使用值 `022` 在 `magento_umask` 檔案，亦即：

* 755 for directories：使用者的完全控制許可權，其他人都可周遊目錄。
* 644 （適用於檔案）：使用者的讀寫許可權，其他所有人皆為唯讀。

要設定 `magento_umask`：

1. 在命令列終端機中，以 [檔案系統擁有者](../prerequisites/file-system/overview.md).
1. 瀏覽至應用程式安裝目錄：

   ```bash
   cd <Application install directory>
   ```

1. 使用以下命令建立名為的檔案 `magento_umask` 並撰寫 `umask` 值。

   ```bash
   echo <desired umask number> > magento_umask
   ```

   您現在應有一個名為的檔案 `magento_umask` 在 `<Magento install dir>` 唯一的內容為 `umask` 數字。

1. 登出並重新登入為 [檔案系統擁有者](../prerequisites/file-system/overview.md) 以套用變更。
