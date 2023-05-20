---
title: 雲端基礎結構概覽
description: 瞭解雲端基礎結構上的Adobe Commerce。
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
source-git-commit: ea912c48176fb060e48654d05ae6b533436a2432
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# 概觀

Adobe Commerce本身提供AWS上Adobe Commerce最受歡迎的受管理託管選項之一。 雲端基礎結構上的Adobe Commerce是適用於Adobe Commerce軟體的完全受管理的自動化託管平台。

雲端基礎結構上的Adobe Commerce是一項平台即服務(PaaS)產品，可讓您快速部署完全可自訂、安全且可擴展的Web店面，並結合領先的託管及受管服務基礎結構。 它提供兩種具有不同基礎結構的計畫。 Adobe Commerce Starter最適合具有較低複雜性和較小目錄的小型商店。 Adobe Commerce Pro專為較複雜、產品目錄較大或流量尖峰的大型商店所打造。 Adobe Commerce會利用合作夥伴的意見來決定適當的架構。

Adobe Commerce具備雲端就緒，並具備完整備援的多雲端託管基礎架構，提供最佳化的效能、彈性和彈性擴充性。 您可以在Fastly的內容傳遞網路(CDN)上有效率地執行您的商務平台，並透過New Relic進行監控和管理，讓您的商店環境得以順暢運作。

Adobe Commerce提供現代雲端運算的所有優點，這些優點最常與SaaS解決方案相關聯：彈性擴充性、高復原力和可用性、PCI法規遵循、全球可用性及自動修補，同時仍維持商家所需的軟體客製化彈性。

![在雲端基礎結構上顯示Adobe Commerce架構元素的圖表](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## 優點

Adobe Commerce的其他優點包括：

- **針對Adobe Commerce最佳化**. Adobe Commerce開發的組建指令碼和服務設定可確保正確調整並設定每個執行個體，以獲得最佳商家效能。

- **一致、安全的發行版本**. 所有程式碼部署都以Git為基礎，以保持一致性和可重複性，並具備唯讀生產環境，提供強化的安全性。

- **合作夥伴的彈性**. 完整的REST API和可編寫指令碼的命令列介面可確保與外部系統輕鬆整合，並與現有的程式碼管理工作流程相容。

- **彈性的部署工具集**. 可隨時快速加速、合併、複製和拆除無限環境，以執行開發任務、QA測試或生產問題診斷。

- **持續雲端傳送**. 您可以放心地跨程式碼分支和開發團隊連續地從開發邁向UAT邁向生產。

## 協力廠商服務

我們也來看看讓Adobe Commerce的好處成為現實的軟體。

![在雲端基礎結構技術棧疊上顯示Adobe Commerce的圖表](../../../assets/playbooks/cloud-tech-stack.svg)

- Fastly CDN：當客戶存取您的網站和商店時，請求點選Fastly以更快載入快取頁面。 Fastly WAF也提供DDoS保護服務。

- New Relic可讓您完整檢視應用程式和作業環境。 它可讓您結合行動應用程式和瀏覽器應用程式的關鍵量度與支援服務、資料存放區和主機，以便整體最佳化效能並確保每個計畫的成功。

- Composer會管理Adobe Commerce中的相依性和升級，並提供所包含套件的相關情境、套件作用以及套件如何整合。

- Git是您在存放庫中的程式碼。 它允許本機分支、便利的臨時區域，以及具備自動建置和部署的多個工作流程，以實現高效的快速開發和持續部署。

- Platform-as-a-Service (PaaS)提供預先布建的基礎結構，包括PHP、MySQL、Redis、 [!DNL RabbitMQ]和OpenSearch或Elasticsearch技術。

- AWS或Azure的雲端主機支援基礎基礎結構即服務(IaaS)，提供可擴充且安全的環境，適合線上銷售和零售。
