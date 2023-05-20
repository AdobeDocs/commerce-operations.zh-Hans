---
title: 雲端基礎結構環境
description: 針對正確的使用案例使用正確的環境。
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 環境

雲端基礎結構上的Adobe Commerce Pro架構支援可用於開發、測試和啟動您的商店的環境。 每個環境都包含一個資料庫和一個Web伺服器。 Adobe Commerce使用的四個環境包括：

- **整合** — 提供單一環境分支，您最多可以建立四個額外的環境分支。 這允許將最多五個使用中分支部署至Platform-as-a-Service (PaaS)容器。

- **分段** — 提供部署至專用基礎架構即服務(IaaS)容器的單一環境分支。

- **生產** — 提供部署至專用基礎架構即服務(IaaS)容器的單一環境分支。

- **全域主版** — 提供部署至Platform-as-a-Service (PaaS)容器的主分支。

![顯示Adobe Commerce雲端環境之間關係的圖表](../../../assets/playbooks/environment-diagram.svg)

## Git分支

整合環境提供單一基本整合分支，其中包含部署至Platform-as-a-Service (PaaS)容器的Adobe Commerce程式碼。

雲端基礎結構環境上的Adobe Commerce支援靈活、持續的整合程式。 從複製整合分支至本機專案資料夾開始。 建立新分支或多個分支，以開發新功能、設定變更和新增擴充功能。 透過已開發的程式碼分支和相應的設定檔案，您的程式碼變更可以合併到整合分支，以進行更全面的測試。

![圖表顯示Adobe Commerce雲端環境的Git型分支策略](../../../assets/playbooks/branching-diagram.svg)
