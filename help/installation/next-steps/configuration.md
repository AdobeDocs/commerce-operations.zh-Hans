---
title: 設定應用程式
description: 瞭解Adobe Commerce和Magento Open Source內部部署所需的安裝後設定。
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# 設定應用程式

現在您已安裝Adobe Commerce或Magento Open Source，您需要進行設定。 本主題提供一些建議的組態設定。

## 設定cron

UNIX工作排程器cron對應用程式的日常作業至關重要。 它會排程重新索引、電子報、電子郵件和網站地圖。 A *crontab* 是cron設定。

您必須安裝Adobe Commerce和Magento Open Source服務，於 *crontab*&#x200B;或某些核心功能（以及某些協力廠商擴充功能）無法正常運作。

如需cron的詳細資訊，包括如何從命令列移除crontab及執行cron，請參閱 [設定並執行cron](../../configuration/cli/configure-cron-jobs.md).

## 安全性設定和建議

安裝後，我們建議使用下列專案：

* 請確定您的檔案擁有權和許可權已正確設定
* 我們強烈建議 [變更預設管理員URI](../tutorials/admin-uri.md) 從 `admin` 至其他內容
* 確定 [`X-Frame-Option` HTTP標頭](../../configuration/security/xframe-options.md) 已正確設定。
* 針對跨網站指令碼(XSS)採取預防措施，措施如下： [保護範本](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

若您由以下人員安裝： [複製GitHub存放庫](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)，請確定在部署應用程式時，您僅包含生產環境所需的檔案和資料夾。 不需要的檔案和資料夾可能會帶來安全性風險。

## 啟用Apache伺服器重寫

如果您使用Apache Web Server，則必須啟用伺服器重新寫入，才能正確顯示頁面。 否則，您會看到沒有樣式和其他問題的頁面。

[有關Apache伺服器重寫的區段](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## 多Webnode環境中的快取

如果您有多個網頁節點，您可以 *無法* 使用應用程式的預設檔案快取，因為Web節點之間沒有同步化。 換言之，一個Web節點上的活動只會寫入該Web節點的檔案系統。 如果在其他網頁節點上執行後續活動，可能會導致寫入不必要的檔案，或導致錯誤。

請改用 [Redis](../../configuration/cache/config-redis.md) 預設快取和頁面快取的。

## 伺服器設定

本節簡要討論建議您在應用程式執行所在的伺服器上考慮的設定。 其中有些設定並未與應用程式直接相關；這些僅以建議形式提供。

### 記錄輪換

UNIX `logrotate` 公用程式可讓您管理產生大量記錄檔的系統。 它允許自動旋轉、壓縮、移除和郵寄記錄檔。 每個記錄檔都可每日、每週、每月或當記錄檔超過指定大小時處理。

如需詳細資訊，請參閱下列其中一項：

* [HowTo： ultimate log rotate命令教學課程，包含10個範例](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [棧疊交換](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` 線上手冊](https://linuxconfig.org/logrotate-8-manual-page)

### 設定iptables規則以啟用各種服務通訊

無論您有一台或多台伺服器，您都必須開啟防火牆中的連線埠，才能讓服務能夠通訊。 例如，如果您將Solr搜尋引擎與Adobe Commerce搭配使用，則必須啟用它以與網頁伺服器通訊。 如果您有多個Web節點，則必須啟用它們來彼此通訊。

更多資訊：

* Ubuntu： [Ubuntu檔案頁面](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS： [CentOS操作說明](https://wiki.centos.org/HowTos/Network/IPTables).

### 安全性增強的Linux (SELinux)規則

我們沒有關於是否使用SELinux的建議；但是，如果您確實使用它，則必須設定服務以便彼此通訊，類似於設定iptables。

更多資訊：

* Ubuntu： [Debian手冊](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS： [CentOS wiki](https://wiki.centos.org/HowTos/SELinux)

### 設定電子郵件伺服器

Adobe Commerce和Magento Open Source需要電子郵件伺服器。 我們不建議使用特定伺服器，但您可以嘗試下列任何一項：

* CentOS的字尾([數位海洋教學課程](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6)， [CentOS檔案](https://www.centos.org))
* Ubuntu的字尾([數位海洋教學課程](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04)， [Ubuntu檔案](https://help.ubuntu.com/community/MailServer))

### 調整搜尋引擎以提升效能：

自2.4.0版起，所有安裝都需要Elasticsearch或OpenSearch。

* [安裝及設定搜尋引擎](../../configuration/search/overview-search.md)

### 設定訊息佇列

自2.3.0版開始，Adobe Commerce和Magento Open Source都包含訊息佇列功能。 在舊版中，它僅適用於Adobe Commerce。

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## 僅適用於Adobe Commerce的設定

只有在使用Adobe Commerce時才能設定下列專案：

* [分割用於簽出、訂單管理和其他資料庫表格的資料庫](../../configuration/storage/multi-master.md)
