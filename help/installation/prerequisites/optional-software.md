---
title: 選購軟體
description: 進一步瞭解您可以安裝的選用軟體，以支援Adobe Commerce和Magento Open Source的內部安裝。
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# 選購軟體

強烈建議您安裝NTP，以確保cron相關工作可正確執行。 （例如，伺服器日期可以是過去或未來的日期。）

本主題中討論的其他選用公用程式可協助您進行安裝；不過，安裝或使用Adobe Commerce或Magento Open Source並不需要這些公用程式。

## 安裝和設定網路時間通訊協定(NTP)

[NTP](https://www.ntp.org/) 可讓伺服器使用同步處理其系統時鐘 [全域可用的集區伺服器](https://www.ntppool.org/en/). 我們建議您使用您信任的NTP伺服器，不論是您內部網路或外部公用伺服器的專用硬體解決方案。

如果您要在多部主機上部署Adobe Commerce或Magento Open Source，NTP是保證所有伺服器時鐘都同步的簡單方法，無論伺服器處於哪個時區。 此外，cron相關工作（例如索引和異動電子郵件）取決於伺服器時鐘是否準確。

### 在Ubuntu上安裝和設定NTP

輸入下列命令以安裝NTP：

```bash
apt-get install ntp
```

繼續使用 [使用NTP集區伺服器](#use-ntp-pool-servers).

### 在CentOS上安裝和設定NTP

若要安裝及設定NTP：

1. 輸入下列命令以尋找適當的NTP軟體：

   ```bash
   yum search ntp
   ```

1. 選取要安裝的套件。 例如， `ntp.x86_64`.

1. 安裝套件。

   ```bash
   yum -y install ntp.x86_64
   ```

1. 輸入下列命令，讓NTP在伺服器啟動時啟動。

   ```bash
   chkconfig ntpd on
   ```

1. 繼續下一節。

### 使用NTP集區伺服器

選擇集區伺服器由您決定。 如果您使用NTP集區伺服器，ntp.org建議您使用 [集區伺服器](https://www.ntppool.org/en/) 接近伺服器時區的時區，如 [NTP集區專案頁面](https://www.ntppool.org/en/use.html). 如果您有可供部署中所有主機使用的私人NTP伺服器，您可以改用該伺服器。

1. 開啟 `/etc/ntp.conf` 在文字編輯器中。

1. 尋找類似下列的行：

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. 取代這些行，或新增指定您的NTP集區伺服器或其他NTP伺服器的其他行。 最好指定多個。

1. 以下是使用三個以美國為基礎的NTP伺服器的範例：

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. 將變更儲存至 `/etc/ntp.conf` 並退出文字編輯器。

1. 重新啟動服務。

   * Ubuntu： `service ntp restart`

   * CentOS： `service ntpd restart`

1. 輸入 `date` 以檢查伺服器的日期。

   如果日期不正確，請確定NTP使用者端連線埠（通常是UDP 123）已在防火牆中開啟。

   請嘗試 `ntpdate _[pool server hostname]_` 命令。 如果失敗，請搜尋它傳回的錯誤。

   如果其他所有操作失敗，請嘗試重新啟動伺服器。

## 建立phpinfo.php

此 [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) 檔案會顯示大量有關PHP及其副檔名的資訊。

>[!NOTE]
>
>使用 `phpinfo.php` 在開發系統中 _僅限_. 這可能是生產環境的安全問題。

將下列程式碼新增至網頁伺服器docroot中的任何位置：

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

如需詳細資訊，請參閱 [phpinfo手動頁面](https://www.php.net/manual/en/function.phpinfo.php).

若要檢視結果，請在瀏覽器的位置或位址欄位中輸入下列URL：

```http
http://<web server host or IP>/phpinfo.php
```

如果顯示404 （找不到）錯誤，請檢查下列專案：

* 視需要啟動網頁伺服器。
* 請確定您的防火牆允許連線埠80上的流量。

   [Ubuntu說明](https://help.ubuntu.com/community/UFW)

   [CentOS說明](https://wiki.centos.org/HowTos/Network/IPTables)

## phpMyAdmin

phpMyAdmin應用程式是易於使用的免費資料庫管理公用程式。 您可以使用它來檢查並操作資料庫的內容。 您必須以MySQL資料庫管理使用者的身分登入phpMyAdmin。

如需phpMyAdmin的詳細資訊，請參閱 [phpMyAdmin首頁](https://www.phpmyadmin.net/).

如需有關安裝的詳細資訊，請參閱 [phpMyAdmin安裝檔案](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>在開發系統中使用phpMyAdmin _僅限_. 這可能是生產環境的安全問題。

1. 若要使用phpMyAdmin，請在瀏覽器的位址或位置欄位中輸入以下命令：

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. 出現提示時，使用您的MySQL資料庫登入 `root` 或管理使用者的使用者名稱和密碼。
