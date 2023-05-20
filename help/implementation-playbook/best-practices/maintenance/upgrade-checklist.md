---
title: 升級檢查清單最佳實務
description: 瞭解如何建立並使用升級檢查清單來規劃Adobe Commerce和Magento Open Source升級策略。
role: Leader
feature: Best Practices
feature-set: Commerce
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 升級檢查清單最佳實務

在與電子商務團隊進行年度和季度對話時，使用此檢查清單。 許多公司使用年度預算與藍圖。 在這些年度討論中，您必須談論平台的健康狀況、發展方向及年度升級策略，以及平台如何配合業務的整體目標及KPI。 在季度交談中，請確認您建立的年度計畫仍然符合您目前的情況，若未符合的話，請樞紐分析。 此升級計畫檢查清單的目標是協助您規劃和排程Adobe Commerce升級，以確保該年度升級流程成功。 此檢查清單旨在由以下對象用於年度規劃和季度審查：

- Director /管理IT
- 電子商務管理員
- 解決方案合作夥伴/顧問

>[!NOTE]
>
>有關成功升級的技術步驟的詳細說明，請參閱 [完成升級必備條件](../../../upgrade/prepare/prerequisites.md) （位於我們的使用者檔案中）。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 目標

▢檢閱目前的KPI，並視需要調整。

## 擴充功能與自訂

▢檢閱所有目前的擴充功能和自訂專案，並根據業務需求確定仍需使用這些專案。

▢請考慮替換任何沒有良好追蹤記錄以保持最新版本的Adobe Commerce擴充功能。

## 團隊

▢確保您擁有合適的團隊，且擁有適當的Adobe Commerce認證和技能組合。

## 預算與時間

▢使用Adobe Commerce [發行排程](../../../release/schedule.md) 以規劃您的下一次升級，並提前準備。

▢根據預期需求，討論您認為將會採用哪個版本（完整或僅限安全性）。

▢預留預算與團隊容量以進行升級。

## 協力廠商整合

▢檢閱當年的Adobe Commerce協力廠商整合及其維護期間，並考慮將升級工作與維護排程進行協調。

## 範圍與部署規劃

提▢搶先體驗活動

- 合作夥伴參與 [Beta](../../../release/beta.md)
- Beta版發行說明稽核。

▢議定預算、時間表、範圍。

▢執行 [升級相容性工具](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢請考慮使用升級來解決由下列識別的問題： [全網站分析工具](../../../tools/site-wide-analysis-tool/intro.md).

▢檔案相依性及任何所需的技術棧疊變更，例如PHP或Elastic Search版本。

▢透過Adobe Commerce認證收集專案團隊。

▢建立利害關係人溝通計畫。

▢如果預期停機，則規劃維護期間。

▢檢閱及核准測試策略；考慮使用Adobe Commerce [測試架構](https://developer.adobe.com/commerce/testing/) 或協力廠商自動化套裝。

▢確認所有擴充功能和自訂內容都相容。

▢檢閱並更新上市後行動手冊；以在升級期間或升級後發現問題時使用。

## 部署後

▢監視網站是否有問題 — 效能、訂單處理、分析等。

▢執行Adobe Commerce [安全性掃描](https://account.magento.com/scanner/dashboard/) 或其他協力廠商掃描並檢閱潛在的安全性弱點。

▢與所有利害關係人執行回顧式研究，並記錄哪些專案進展順利、哪些專案失敗以及如何改進。

▢透過所學的課程修改您的下一次升級計畫。
