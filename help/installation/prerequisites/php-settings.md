---
title: PHP設定
description: 請依照下列步驟安裝必要的PHP擴充功能，並為Adobe Commerce和Magento Open Source的內部部署設定必要的PHP設定。
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# PHP設定

本主題討論如何設定必要的PHP選項。

>[!NOTE]
>
>另請參閱 [系統需求](../system-requirements.md) 支援的PHP版本。

## 驗證是否已安裝PHP

大部分的Linux版本預設會安裝PHP。 本主題假設您已安裝PHP。 若要驗證是否已安裝PHP，請在指令行中鍵入：

```bash
php -v
```

如果已安裝PHP，則會顯示類似於以下內容的訊息：

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe Commerce和Magento Open Source2.4與PHP 7.3相容，但我們使用PHP 7.4進行測試，並建議使用。

如果未安裝PHP，或需要版本升級，請按照針對您的特定Linux風格的說明進行安裝。
在CentOS上， [可能需要其他步驟](https://wiki.centos.org/HowTos/php7).

## 驗證已安裝的擴充功能

Adobe Commerce和Magento Open Source需要安裝一組擴充功能。

{{$include /help/_includes/templated/php-extensions.md}}

若要驗證已安裝的擴充功能：

1. 列出已安裝的模組。

   ```bash
   php -m
   ```

1. 確認已安裝所有必要的擴充功能。
1. 使用用於安裝PHP的相同工作流程來新增任何缺少的模組。 例如，如果您使用 `yum` 若要安裝PHP，可將PHP 7.4模組加入以下程式碼：

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## 檢查PHP設定

>[!WARNING]
>
>如果您使用PHP 7.4.20，請設定 `pcre.jit=0` 在您的 `php.ini` 檔案。 這會繞過PHP [錯誤](https://bugs.php.net/bug.php?id=81101) 可防止CSS載入。

- 設定PHP的系統時區；否則，在安裝期間顯示以下錯誤，以及cron等時間相關操作可能無法運作：

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- 設定PHP記憶體限制。

   我們的詳細建議包括：

   - 編譯程式碼或部署靜態資產， `1G`
   - 偵錯， `2G`
   - 測試， `~3-4G`

- 增加PHP的值 `realpath_cache_size` 和 `realpath_cache_ttl` 至建議的設定：

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   這些設定可讓PHP處理序快取檔案的路徑，而不是在每次頁面載入時查詢它們。 另請參閱 [效能調整](https://www.php.net/manual/en/ini.core.php) PHP檔案中。

- 啟用 [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments)，此為Adobe Commerce和Magento Open Source 2.1及更新版本的必要專案。

   建議您啟用 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) 基於效能考量。 OPcache已在許多PHP發行版本中啟用。

   Adobe Commerce和Magento Open Source2.1及更高版本使用PHP程式碼註解來產生程式碼。

>[!NOTE]
>
>為避免在安裝和升級期間出現問題，強烈建議您對PHP命令列配置和PHP Web伺服器外掛程式配置都套用相同的PHP設定。 如需詳細資訊，請參閱下一節。

## 尋找PHP組態檔

本節將討論如何找到更新所需設定所需的組態檔。

### 尋找 `php.ini` 設定檔

若要尋找網頁伺服器組態，請執行 [`phpinfo.php` 檔案](optional-software.md#create-phpinfophp) 在網頁瀏覽器中尋找 `Loaded Configuration File` 如下所示：

![PHP資訊頁](../../assets/installation/config_phpini-webserver.png)

若要找到PHP命令列組態，請輸入

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>如果您只有一個 `php.ini` 檔案中，在該檔案中進行變更。 如果您有兩種 `php.ini` 檔案，變更於 *全部* 檔案。 若未這麼做，可能會導致無法預測的效能。

### 尋找OPcache組態設定

PHP OPcache設定通常位於 `php.ini` 或 `opcache.ini`. 位置可能取決於您的作業系統和PHP版本。 OPcache設定檔可能有 `opcache` 區段或設定，例如 `opcache.enable`.

請使用下列准則來尋找它：

- Apache Web Server：

   對於具有Apache的Ubuntu，OPcache設定通常位於 `php.ini` 檔案。

   對於具有Apache或nginx的CentOS，OPcache設定通常位於 `/etc/php.d/opcache.ini`

   如果沒有，請使用以下命令來尋找它：

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- 使用PHP-FPM的nginx網頁伺服器： `/etc/php/7.2/fpm/php.ini`

如果您有多個 `opcache.ini`，修改所有變數。

## 如何設定PHP選項

若要設定PHP選項：

1. 開啟 `php.ini` 在文字編輯器中。
1. 在可用的中找到伺服器的時區 [時區設定](https://www.php.net/manual/en/timezones.php)
1. 找到下列設定，並視需要取消註解：

   ```conf
   date.timezone =
   ```

1. 新增您在步驟2中找到的時區設定。

1. 變更值 `memory_limit` 變更為本節開頭建議的其中一個值。

   例如，

   ```conf
   memory_limit=2G
   ```

1. 新增或更新 `realpath_cache` 設定以符合下列值：

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. 儲存變更並退出文字編輯器。

1. 開啟另一個 `php.ini` （如果兩者不同）並在其中進行相同的變更。

## 設定OPcache選項

要設定 `opcache.ini` 選項：

1. 在文字編輯器中開啟OPcache設定檔案：

   - `opcache.ini` (CentOS)
   - `php.ini` （烏班圖）
   - `/etc/php/7.2/fpm/php.ini` (nginx網頁伺服器（CentOS或Ubuntu）)

1. 尋找 `opcache.save_comments` 並視需要取消註解。
1. 確保其值設定為 `1`.
1. 儲存變更並退出文字編輯器。
1. 重新啟動網頁伺服器：

   - Apache、Ubuntu： `service apache2 restart`
   - Apache、CentOS： `service httpd restart`
   - Nginx、Ubuntu和CentOS： `service nginx restart`

## 疑難排除

請參閱下列Adobe Commerce支援文章，以取得疑難排解PHP問題的說明：

- [在瀏覽器中存取Adobe Commerce時發生PHP版本錯誤或404錯誤](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP設定錯誤](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP Mcrypt擴充功能未正確安裝](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP版本整備檢查問題](https://support.magento.com/hc/en-us/articles/360033546411)
- [常見PHP嚴重錯誤與解決方案](https://support.magento.com/hc/en-us/articles/360030568432)
