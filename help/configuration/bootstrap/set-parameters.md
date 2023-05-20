---
title: 設定啟動程式引數的值
description: 瞭解如何為Commerce應用程式設定啟動引數。
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# Bootstrap引數

本主題示範如何設定Commerce應用程式啟動引數值。 另請參閱 [應用程式初始化和啟動載入概觀](initialization.md).

下表討論您可以設定的啟動程式引數：

| Bootstrap引數 | 說明 |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | 指定自訂目錄和URL路徑 |
| MAGE_PROFILER | 啟用相依性圖表和HTML設定檔 |

>[!INFO]
>
>- 並非所有啟動程式引數都已記錄下來。
>- 您現在可以使用以下設定應用程式模式（開發人員、預設、生產）： [`magento deploy:mode:set {mode}`](../cli/set-mode.md) 命令。


## 使用環境變數設定引數

本節探討如何使用環境變數設定啟動程式引數的值。

### 設定應用程式模式

您可以將啟動載入變數指定為系統範圍的環境變數，讓所有程式都可以使用這些變數。

例如，您可以使用 `MAGE_PROFILER` 系統環境變數來指定模式，如下所示：

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

使用殼層特定指令設定變數。 由於shell的語法不同，請參考參考如 [unix.stackexchange.com][unix-stackx].

CentOS的Bash shell範例：

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>若為 `PHP Fatal error` 設定效能評測器值後，就會顯示在瀏覽器中，請重新啟動網頁伺服器。 原因可能與PHP位元組碼快取有關，它會快取位元組碼和PHP類別路徑。

## 設定Apache或Nginx的引數

本節討論如何指定Apache或Nginx的模式。

### Nginx設定

請參閱 [Nginx範例設定] 於 _GitHub_.

### Apache .htaccess設定

設定應用程式模式的一種方法是編輯 `.htaccess`. 如此一來，您就不必變更Apache設定。

您可以修改 `.htaccess` 在下列任一位置（視您的Commerce應用程式進入點而定）：

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**若要設定變數**：

1. 在文字編輯器中開啟任何先前的檔案，然後新增或取消註解所需的設定。

   例如，若要指定 [模式](application-modes.md)，取消註解以下內容：

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. 設定值 `MAGE_PROFILER` 變更為下列任一專案：

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. 將變更儲存至 `.htaccess`；您不需要重新啟動Apache變更即可生效。

### Apache設定

Apache Web Server支援使用設定應用程式模式 `mod_env` 指令。

Apache `mod_env` 指示詞在以下內容中稍微不同： [Apache 2.2版] 和 [Apache 2.4版].

以下程式說明如何在Apache虛擬主機中設定應用程式模式。 這不是唯一的使用方式 `mod_env` 指示詞；如需詳細資訊，請參閱Apache檔案。

>[!TIP]
>
>下節假設您已設定虛擬主機。 如果沒有，請查閱資源，例如 [此DigitalOcean教學課程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**為Ubuntu上的Apache指定啟動載入變數**：

1. 作為使用者，具有 `root` 許可權，在文字編輯器中開啟您的虛擬主機設定檔案。

   例如，如果您的虛擬主機名為 `my.magento`，

   - Apache 2.4： `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2： `vim /etc/apache2/sites-available/my.magento`

1. 在虛擬主機設定的任何位置，新增下列行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   例如，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 儲存變更並退出文字編輯器。
1. 啟用虛擬主機（如果尚未啟用）：

   ```bash
   a2ensite <virtual host config file name>
   ```

   例如，

   ```bash
   a2ensite my.magento.conf
   ```

1. 設定模式後，請重新啟動網頁伺服器：

   - Ubuntu： `service apache2 restart`
   - CentOS： `service httpd restart`

>[!TIP]
>
>本節假設您已設定虛擬主機。 如果沒有，請查閱資源，例如 [此DigitalOcean教學課程](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**若要為CentOS上的Apache指定啟動載入變數**：

1. 作為使用者，具有 `root` 許可權，開啟 `/etc/httpd/conf/httpd.conf` 在文字編輯器中。

1. 在虛擬主機設定的任何位置，新增下列行：

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   例如，

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. 儲存變更並退出文字編輯器。

1. 設定模式後，請重新啟動網頁伺服器：

   - Ubuntu： `service apache2 restart`
   - CentOS： `service httpd restart`

<!-- link definitions -->

[Apache 2.2版]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache 2.4版]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx範例設定]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
