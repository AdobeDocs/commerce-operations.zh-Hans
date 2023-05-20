---
title: 建立資料移轉計畫
description: 請依照下列步驟建立資料移轉計畫，以確保成功從Magento1升級至Magento2。
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# 建立資料移轉計畫

若要成功移轉並避免問題，您必須徹底規劃並測試移轉。

## 開始之前：請考慮升級

移轉是進行重大變更的絕佳時機，可讓您的網站為下一層級的成長做好準備。 考慮您的新網站在設計上是否需要更多硬體，或是更進階的拓撲，以及更好的快取階層。

## 步驟1：檢閱目前網站上的擴充功能

* 您已安裝哪些擴充功能？

* 您是否已確定新網站上是否需要所有這些擴充功能？ 可能有您可以安全移除的舊專案。

* 您是否已確定您的擴充功能是否存在Magento2版本？ 造訪 [Commerce Marketplace] 以尋找最新版本，或聯絡您的擴充功能提供者。

* 您要移轉擴充功能中的哪些資料庫資產？

## 步驟2：建立並準備要移轉的存放區

* 使用至少符合您現有Magento1系統的拓撲和設計來設定Magento2硬體系統

* 安裝Magento2.x （包含此版本的所有模組）和 [!DNL Data Migration Tool] 在符合 [系統需求](../../installation/system-requirements.md)

* 對進行自訂調整 [!DNL Data Migration Tool] 代碼，以備您不需要移轉部分資料（例如CMS Pages、Sales Rules）或想要在移轉期間轉換Magento自訂時使用。 閱讀 [!DNL Data Migration Tool]的 [技術規格](technical-specification.md) 以更清楚瞭解移轉作業如何從內部運作

## 步驟3：試用

在生產環境中開始移轉之前，最好先在測試環境中完成所有移轉步驟。

在此等移轉測試中，請遵循下列步驟：

* 將您的Magento1存放區複製到中繼伺服器

* 將複製的Magento1存放區完全移轉至Magento2

* 徹底測試您的新商店

## 步驟4：開始移轉

1. 請確定 [!DNL Data Migration Tool] 具有網路存取權，可連線至Magento1和Magento2資料庫。 開啟防火牆中對應的連線埠。

1. 停止「Magento1.x管理面板」中的所有作業（訂單管理除外），例如出貨、建立商業發票及銷退折讓單。 您可以調整「 」中「差異」模式的設定，以擴充允許的活動清單。 [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >您必須等到Magento2存放區上線後，才能繼續這些活動。

1. 我們建議停止所有Magento1.x cron工作。

   不過，如果在移轉期間需要執行某些工作，請確定它們不會建立新的資料庫實體，或變更現有實體，以免這些實體無法以Delta模式處理。

   例如， `enterprise_salesarchive_archive_orders` cron job會移動要封存的舊訂單。 在移轉期間執行此作業是安全的，因為差異模式可辨識此作業並正確處理已封存的訂單。

1. 使用 [!DNL Data Migration Tool] 移轉設定和網站。

1. 將您的Magento1.x媒體檔案複製到Magento2.x。

   您必須從以下位置手動複製這些檔案 `magento1-root/media` 目錄至 `magento2-root/pub/media`.

1. 使用 [!DNL Data Migration Tool] 將資料從Magento1資料庫大量複製到Magento2資料庫。

   如果部分擴充功能含有您要移轉的資料，您可能需要安裝這些適用於Magento2的擴充功能。 如果Magento2資料庫中的擴充功能具有不同的結構，請使用隨附的對映檔案 [!DNL Data Migration Tool].

1. 重新索引所有Magento2.x索引子。 如需詳細資訊，請參閱 [管理索引子](../../configuration/cli/manage-indexers.md) 在 _設定指南_.

## 步驟5：視需要對移轉的資料進行變更

有時候，您可能會想要在移轉後，讓Magento2存放區具有不同的目錄結構、銷售規則和CMS頁面。

進行手動資料變更時，請務必謹慎操作。 錯誤會在後續的增量資料移轉步驟中造成錯誤。

例如，從Magento2中刪除的產品：已在即時Magento1商店中購買且在您的Magento2商店中不再可用的產品。 傳輸有關此類購買的資料可能會在執行時造成錯誤 [!DNL Data Migration Tool] 在差異模式中。

## 步驟6：更新增量資料

移轉資料後，您必須逐步擷取Magento1存放區中已新增的資料更新（例如新訂單、評論和客戶設定檔中的變更），並使用差異模式將這些更新傳輸到Magento2存放區。

* 開始增量移轉；更新會持續執行。 您可以隨時按以停止傳輸更新 `Ctrl+C`.

* 在此期間，請測試您的Magento2網站，以儘快找出任何問題。 如果您遇到問題，請按 `Ctrl+C` 停止增量移轉，並在您解決問題後重新啟動。

>[!NOTE]
>
>如果您同時執行Magento2網站測試和執行移轉程式，可能會出現大量檢查警告。 發生這種情況是因為在Magento2中，您會建立在Magento1例項中不存在的實體。

## 步驟7：上線

現在您的Magento2網站已與Magento1保持同步且正常運作，請執行以下操作以切換至新網站：

1. 將Magento1系統置於維護模式（停機時間開始）。

1. 在移轉工具命令視窗中按Control+C可停止增量更新。

1. 開始您的Magento2 cron工作。

1. 在您的Magento2系統中，重新索引股票索引器。 如需詳細資訊，請參閱 [設定指南].

1. 使用您選擇的工具，在客戶使用您的店面之前，點選Magento2系統中的頁面以快取頁面。

1. 對您的Magento2網站執行任何最終驗證。

1. 變更DNS、負載平衡器等，以指向新的生產硬體(DOWNTIME ENDS)。

1. Magento2商店現在已可供使用。 您和您的客戶可以恢復所有活動。

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
