---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# 安全的Web伺服器通訊

Elasticsearch本主題說明如何結合使用傳輸層安全性(TLS)加密與 [HTTP基本驗證](https://datatracker.ietf.org/doc/html/rfc2617). 您也可以選擇設定其他型別的驗證；我們提供該資訊的參考。

(舊稱Secure Sockets Layer (SSL)，經常與TLS互換使用。 在本主題中，我們參照 *TLS*.)

>[!WARNING]
>
>除非另有說明，否則本主題中的所有命令都必須以使用者身分輸入， `root` 許可權。

## Recommendations

我們建議採取下列步驟：

* 您的網頁伺服器使用TLS。

   TLS不在本主題的討論範圍內；不過，強烈建議您使用實際憑證，而非自行簽署憑證。

* 您的搜尋引擎會在與網頁伺服器相同的主機上執行。 在不同主機上執行搜尋引擎和網頁伺服器不在本主題的討論範圍內。

   將搜尋引擎和網頁伺服器放在同一台主機上的好處是，它無法攔截加密的通訊。 搜尋引擎網頁伺服器不必與Adobe Commerce或Magento Open Source網頁伺服器相同；例如，Adobe Commerce可以執行Apache，而Elasticsearch/OpenSearch可以執行nginx。

   如果搜尋引擎公開於公用網路，您應設定驗證。 如果您的搜尋引擎執行個體在網路上受到保護，則可能不需要這樣做。 請與您的託管提供者合作，決定您應實作哪些安全性措施來保護執行個體。

## 有關TLS的更多資訊

請參閱下列資源之一：

* Apache

   * [Apache 2.4高度加密做法](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [如何在Apache for Ubuntu 14.04上建立SSL憑證（數位海洋教學課程）](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [使用CentOS (CentOS wiki)設定SSL安全Web伺服器](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx SSL終止](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [如何在Nginx for Ubuntu 14.04上建立SSL憑證（Digitalocean教學課程）](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL憑證安裝(digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
