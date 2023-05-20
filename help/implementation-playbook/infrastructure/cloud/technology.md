---
title: 雲端基礎結構技術
description: 進一步瞭解我們在雲端基礎結構上用於Adobe Commerce的技術集合。
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: 683ce0a72aca0319ade2e4ccfd7a8e541a228156
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# 技術

如我們先前所述，Adobe Commerce運用許多軟體解決方案來支援該平台。 具體而言，由於與生產相關，我們已在雲端基礎結構上細分Adobe Commerce中包含的一些技術解決方案和功能，這些解決方案和功能有助於充分利用您的生產環境。

![圖表顯示雲端基礎結構技術上的Adobe Commerce](../../../assets/playbooks/infrastructure-technology.svg)

## 軟體解決方案

- **Nginx** — 使用PHP-FPM的網頁伺服器。 有一個執行個體具有多個背景工作。

- **GlusterFS** — 檔案伺服器，用於管理所有靜態檔案部署及四個目錄掛載的同步化：
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis** — 每個VM一台伺服器，只有一個作用中，另外兩個作為復本。

- **Elasticsearch** — 搜尋Adobe Commerce 2.2.x版和更新版本。

- **OpenSearch** — 搜尋Adobe Commerce 2.4.6版和更新版本。

- **Galera** — 資料庫叢集，每個節點有一個MariaDB MySQL資料庫，每個資料庫中唯一ID的自動增加設定為3。

## 功能與優點

- 在VPC中有三個專用執行個體，在三個獨立的可用區域或資料中心間有一個彈性負載平衡器。

- 針對可能導致單一執行個體失敗的事件，提供更高的恢復能力。 例如，整個AWS可用區域或資料中心發生中斷。

- 在15分鐘內完成整個棧疊的零停機時間縮放，包括網頁、快取、搜尋和資料庫。
