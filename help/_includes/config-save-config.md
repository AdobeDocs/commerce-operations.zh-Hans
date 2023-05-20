---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# 更新共用設定

**更新設定的方式**：

1. 以檔案系統擁有者的身分登入或切換到您的開發系統。

1. 變更至應用程式根目錄，然後執行傾印命令。

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   例如，如果商務安裝在中 `/var/www/html/magento2`，輸入：

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. 確認 `app/etc/config.php` 已更新。

   ```bash
   git status
   ```

   範例回應：

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >執行 _not_ 將變更提交至 `generated`， `pub/media`，或 `pub/static` 目錄至原始檔控制。 您會在組建系統上產生這些檔案。 開發系統可能有程式碼、主題等尚未準備好用於生產系統的專案。

1. 將變更籤入 `app/etc/config.php` 僅限原始檔控制。

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
