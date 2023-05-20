---
title: 平台開發原則
description: 瞭解使用Adobe Commerce時的基本平台開發原則。
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# 平台開發原則

在本行動手冊中，我們深入探討Adobe Commerce開發的一些主要標準，包括：

- 符合開發程式的功能和技術範圍
- 符合MVC架構的開發最佳實務
- 架構考量，包括GRA
- 針對指令碼和漏洞的安全性標準
- 擴充功能開發最佳實務
- Web API與REST、SOAP和GraphQL的整合
- 針對編碼和基礎建設的效能改善
- 測試工具、策略和方法

雖然某些解決方案實作者在實施專案中使用的方法、流程和工具方面可能有自己的偏好，但本行動手冊專注於可在大多數實作中分享的公認最佳實務和方法。

像任何大型IT專案一樣，Adobe Commerce建置在編碼標準上，這些標準利用基礎技術(例如PHP/Zend、Symfony、JavaScript、jQuery和HTML)的最佳實務和標準化，以及Adobe Commerce編碼標準中建立的標準。 遵守這些標準絕對是消除錯誤並改善自訂建置計畫碼的品質和可維護性的必要條件。

## 雲端基礎結構上的Adobe Commerce

雲端基礎結構上的Adobe Commerce是適用於Adobe Commerce軟體的受管理、自動化託管平台。 雲端基礎結構上的Adobe Commerce提供多種其他功能，使其有別於內部部署Adobe Commerce和Magento Open Source實施：

![Adobe Commerce元件infographics](../../assets/playbooks/commerce-cloud.svg)

雲端基礎結構上的Adobe Commerce提供預先布建的基礎結構，包括PHP、MySQL、Redis、 [!DNL RabbitMQ]和Elasticsearch技術；以Git為基礎的工作流程，具有自動建置和部署作業，每當在Platform as a Service (PaaS)環境中推送程式碼變更時，都能有效率地進行快速開發和持續部署；可高度自訂的環境設定檔案和工具；以及AWS託管，可為線上銷售和零售提供可擴充且安全的環境。

![Adobe Commerce元件infographics](../../assets/playbooks/cloud-tech-stack.svg)
