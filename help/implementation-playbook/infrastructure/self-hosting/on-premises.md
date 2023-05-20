---
title: 內部部署基礎結構
description: 瞭解Adobe Commerce內部部署基礎結構和第三方雲端服務。
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
source-git-commit: a253da8cfe95083d1df76d3253aaa424b78a4865
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Adobe Commerce內部部署基礎結構

開始新的Adobe Commerce實作或將現有的內部部署Adobe Commerce實作移至雲端的動機很多，但最常見的策略推動因素為減少資本支出、降低持續性成本、改善可擴充性和彈性、縮短上市時間，以及改善安全性與合規性。

下圖顯示在AWS基礎結構上內部部署Adobe Commerce的參考架構。 其他雲端提供者，如Azure、Google Cloud和Alibaba Cloud，擁有類似的基礎架構設計和同類服務。

![在協力廠商雲端服務上自行託管Adobe Commerce基礎結構的圖表](/help/assets/playbooks/on-premises-infrastructure.svg)

讓我們深入探討上述基礎架構各層面的角色和功能：

1. Amazon Route 53提供DNS設定。

1. AWS WAF是Web應用程式防火牆，可保護Adobe Commerce免受常見的Web攻擊。

1. Amazon CloudFront是快速內容傳遞網路(CDN)，可加速靜態和動態網頁內容的發佈。

1. 第一個Elastic Load Balancing應用程式負載平衡器會將Varnish執行個體的流量分配到多個可用區域的AWS Auto Scaling群組中。

1. 清漆快取是網頁應用程式加速器快取HTTP反向Proxy。 建議使用AWS Marketplace提供的企業版本，因為其具備更好的功能，可支援雲端後端和跨動態主機的快取清除。

1. 第二個Elastic Load Balancing應用程式負載平衡器會將來自Varnish快取的流量分散到多個可用區域的Adobe Commerce執行個體的AWS Auto Scaling群組中。

1. 在Amazon EC2執行個體上安裝最新版Magento Open Source或Adobe Commerce。 安裝包括Adobe Commerce應用程式、Nginx Web伺服器和PHP。 建置Amazon機器影像(AMI)以啟動自動縮放群組中的新執行個體。

1. AmazonElasticsearch服務是用於Adobe Commerce目錄搜尋的受管理Elasticsearch服務。

1. 適用於Redis的Amazon ElastiCache提供資料庫的快取階層。

1. 使用Amazon Aurora或AmazonRDS來簡化資料庫管理（包括高可用性和多主機組態）。

1. EFSMount Target有助於將Amazon彈性檔案系統(AmazonEFS)對應到Varnish和Adobe Commerce執行個體。

1. 使用Amazon EFS來存取在Adobe Commerce執行個體之間跨清漆和共用媒體資產的共用設定。

## 雲端服務

除了在您的Adobe Commerce環境周圍的AWS上提供支援DevOps流程的技術平台外，AWS還提供了一組服務，這些服務可提供（在不存在的情況下）或增強您現有的軟體設定管理(SCM)解決方案。 這包括AWSCodeCommit、AWSCodeBuild、AWSCodePipeline和AWSCodeDeploy，後者允許受管理的原始檔控制、建置、持續整合/持續部署(CI/CD)和部署服務。

## 雲端移轉

有數項服務提供營運分析能力及靈活性，進一步提升將Adobe Commerce移轉至AWS的價值主張。 我們的意思是不僅從技術角度（例如每小時請求數）也從業務營運角度（例如每小時訂單數）對平台進行營運分析，尤其是兩套資料可以結合時。 這可提供行銷活動績效、平台營運成本及其他指標近乎無限量的即時資訊。

AWS的Adobe Commerce設定可讓您在雲端中取得完全受管理的替代方案，取代特定的應用程式相依性。 例如，許多應用程式的資料庫可輕易地由Amazon關聯式資料庫服務(AmazonRDS)取代，而不必直接在EC2執行個體上託管關聯式資料庫。 此策略的優點在於，無差異元件的作業責任可以解除安裝至AWS，而不需要大幅變更核心應用程式。

在AWS上執行Adobe Commerce (Magento Open Source和Adobe Commerce版本)有數個部署選項可供使用。 最適合的選擇取決於您在成本、規模、可用性和彈性方面的需求，以及貴組織的AWS和Adobe Commerce技能。

{{$include /help/_includes/hosting-related-links.md}}
