---
title: 系統需求
description: 請使用此參考資料來識別已在Adobe Commerce和Magento Open Source版本中測試過的必要軟體相依性。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# 系統需求

此表格顯示Adobe已透過特定Adobe Commerce和Magento Open Source版本測試的第三方軟體相依性版本。 Adobe僅支援下表所述的系統需求組合。

例如，2.4.5已透過MariaDB 10.4完成測試。Adobe建議您在升級至2.4.5之前，先升級至MariaDB 10.4。

{{$include /help/_includes/templated/system-requirements-table.md}}

## 其他

本節說明所有其他必要和選用軟體型別的支援與相容性。

>[!NOTE]
>
>下列需求適用於Adobe Commerce和Magento Open Source的最新2.4.x修補程式版本。

### 郵件伺服器

郵件傳輸代理程式(MTA)或SMTP伺服器

### 作業系統(Linux x86-64)

Linux發行版本，例如RedHat Enterprise Linux (RHEL)、CentOS、Ubuntu、Debian等。 不支援Microsoft Windows和macOS。

### PHP擴充功能

>[!NOTE]
>
>此 [PHP安裝指示](prerequisites/php-settings.md) 包括安裝這些擴充功能的步驟。

{{$include /help/_includes/templated/php-extensions.md}}

請參閱 [PHP官方檔案](https://php.net/manual/en/extensions.php) 以取得安裝詳細資料。

### PHP OPcache

我們強烈建議您確認 [PHP OPcache](https://php.net/manual/en/intro.opcache.php) 會因為效能原因而啟用。 OPcache已在許多PHP發行版本中啟用。 若要確認是否已安裝，請參閱我們的 [PHP檔案](prerequisites/php-settings.md).

如果您必須另外安裝，請參閱 [PHP OPcache檔案](https://php.net/manual/en/opcache.setup.php).

### PHP設定

我們建議使用特定的PHP組態設定，例如 `memory_limit`，可以避免使用Adobe Commerce和Magento Open Source時的常見問題。

如需詳細資訊，請參閱 [必要的PHP設定](prerequisites/php-settings.md).

### PHPUnit

PHPUnit （作為命令列工具） 9.0.0

### RAM

升級從Commerce Marketplace和其他來源取得的應用程式和擴充功能，最多可能需要2 GB的RAM。 如果您使用的系統RAM小於2 GB，建議您建立 [交換檔案](https://support.magento.com/hc/en-us/articles/360032980432)；否則，升級可能會失敗。

### 系統相依性

Adobe Commerce和Magento Open Source的某些作業需要下列系統工具：

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- HTTPS需要有效的安全性憑證。
- 不支援自我簽署SSL憑證。
- 傳輸層安全性(TLS)需求 — PayPal和 `repo.magento.com` 兩者都需要TLS 1.2或更新版本。

### 支援的瀏覽器

店面和管理：

- Microsoft Edge （最新和先前的主要版本）
- Firefox （最新和舊版主要版本；任何作業系統）
- Chrome （最新和舊版主要版本；任何作業系統）
- Safari (最新和舊版主要版本；僅限macOS)
- 適用於iPad 2的Safari Mobile、iPad Mini、iPad搭配Retina Display (iOS 12或更新版本)、桌麵店面
- 適用於iPhone 6或更新版本的Safari Mobile；適用於行動店面的iOS 12或更新版本
- 適用於行動裝置的Chrome （最新和先前的主要版本） [Android 4或更新版本] 適用於行動店面)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) 或更新版本（僅限開發環境；可能對效能造成不良影響）

>[!NOTE]
>
>有一個已知問題 `xdebug` 可能會影響Adobe Commerce或Magento Open Source安裝或安裝後對店面或管理員的存取許可權。 如需詳細資訊，請參閱 [xdebug的已知問題](https://support.magento.com/hc/en-us/articles/360034242212).
