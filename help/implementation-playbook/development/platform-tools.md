---
title: 平台工具
description: 選擇建議的Adobe Commerce實作平台工具。
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
source-git-commit: ea912c48176fb060e48654d05ae6b533436a2432
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# 平台工具

要確保電子商務網站不受干擾地運作，必須深入思考並嚴格測試各方面。 您不僅必須找出正確的解決方案來處理網站的各個層面（從資料儲存和程式設計，到快取和安全性），而且還需要正確的流程來確保交付的平台既能順暢執行，又能有效率地建置和最佳化。

本節不僅說明在多項Adobe Commerce實作中經過測試和完善的工具、解決方案、流程和方法，也提供我們對於哪些解決方案最符合特定業務需求和目標的建議。

下表包含我們建議的解決方案，可以在Adobe Commerce中使用，藉此提高平台的效能：

| 用途 | 工具 |
|------------------------------------------|-------------------------|
| 資料庫 | MySQL、MariaDB、Percona |
| 程式語言 | PHP、JS、HTML、較少CSS |
| 整合式開發環境(IDE) | Eclipse， PHPStorm |
| 網頁伺服器 | Nginx、Apache |
| 快取服務 | Redis， Varnish |
| 搜尋服務 | Elasticsearch |
| 訊息佇列服務 | [!DNL RabbitMQ] |
| 安全性掃描工具 | SonarQube， ZAP |

## 資料庫

我們根據品牌需求來使用三種不同的工具。 如果您不希望您的存放區處理極端負載，MySQL是Adobe Commerce資料庫的絕佳基準解決方案。

MariaDB以社群為中心，最適合更關注功能（而非純粹效能）的使用者。 MariaDB支援大量資料庫引擎、磁碟加密、複雜的水準互連，以及擴充功能，這些對於大型Adobe Commerce商店來說可能很有趣。

Percona是MySQL的復本，以效能和尖峰負載處理為中心。 如果您需要更優質的生活和DevOps功能，請選擇MariaDB。 如果您的目標是在大型資料集中獲得高負載效能，請改用Percona。

## 程式語言

Adobe Commerce是以PHP為基礎的應用程式，而最新發行版本一律與最新穩定PHP版本相容(例如，Adobe Commerce 2.4版建議使用PHP 7.4)。 為了獲得更高的安全性和效能，在設定PHP以取得請求處理的最大速度和效率時，需要考慮幾個因素。 Adobe Commerce網頁店面是以HTML、JavaScript和LESS CSS前置處理器建置。

## Web伺服器

Adobe Commerce完全支援Nginx和Apache網頁伺服器。 Adobe Commerce提供兩種設定檔的建議設定檔範例：

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Nginx範例包含改善效能的設定，因此不需要重新配置。

## 快取服務

Adobe Commerce提供多種選項來儲存您的快取和工作階段資料，包括Redis、Memcache、檔案系統和資料庫。 若是設定包含多個網頁節點，Redis是最佳選項。

強烈建議您使用Varnish做為商店的全頁快取伺服器。 Adobe Commerce會散發Varnish的設定檔範例，其中包含所有建議的效能設定。

## 搜尋服務

對於Adobe Commerce 2.4版和更新版本，所有安裝都必須設定為使用Elasticsearch或OpenSearch作為目錄搜尋解決方案。 Elasticsearch提供對目錄中產品的快速和進階搜尋。 對於2.4之前的版本，Elasticsearch是選用專案，但建議使用。

## 訊息佇列服務

訊息佇列提供非同步通訊機制，讓訊息的傳送者與接收者不會相互聯絡。 [!DNL RabbitMQ] 是開放原始碼的訊息代理人，提供可靠、高可用性、可擴充且可攜式的訊息系統。

## 安全性工具

此 [Adobe Commerce安全性掃描工具](https://docs.magento.com/user-guide/magento/security-scan.html) 可讓您定期監視商店網站，並接收已知安全性風險、惡意程式碼和過時軟體的更新。 通常，您會在開始使用者驗收測試(UAT)時開始使用此工具。 Adobe Commerce安全性掃描工具是免費的，適用於Adobe Commerce的所有實作和版本，除此之外，您也可以在CI/CD程式期間和每次發行前使用其他選項。

SonarQube是開放原始碼品質管理平台，專為分析和測量程式碼的技術品質而設計。 SonarQube不僅提供程式碼錯誤、語法錯誤和弱點的完整報告，還提供修正程式碼的建議與範例。 SonarQube非常適合在CI/CD環境中使用，作為能夠在部署前分析程式碼的工具。

Zed Attack Proxy (ZAP)是免費的安全性測試工具，全球有數千名筆型測試人員使用。 ZAP由OWASP開發，是手動安全性測試最常用的工具之一。
