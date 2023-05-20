---
title: 資料後移轉步驟
description: 瞭解使用後需要採取哪些步驟 [!DNL Data Migration Tool] 將資料從Magento1移轉至Magento2。
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# 資料後移轉步驟

完成移轉並徹底測試新的Magento2網站後，請執行以下工作：

* 將Magento1置於維護模式，並永久停止所有管理員活動

* 開始Magento2 cron工作

* [排清所有Magento2快取型別](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [重新索引所有Magento2索引器](../../../configuration/cli/manage-indexers.md#reindex)

* 變更DNS和負載平衡器以指向Magento2生產硬體
