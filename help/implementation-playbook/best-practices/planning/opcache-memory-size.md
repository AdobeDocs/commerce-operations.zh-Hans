---
title: OPcache記憶體大小的最佳實務
description: 說明如何避免Adobe Commerce專案中OPcache記憶體消耗的特定設定導致效能下降。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Adobe Commerce中OPcache記憶體大小的最佳實務

針對雲端基礎結構上的Adobe Commerce Pro計畫架構2.3.x，建議設定 `opcache.memory_consumption` 至至少2 GB，以避免效能降低。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce Pro計畫架構2.3.x
* PHP 7.0及更高版本

## 設定記憶體

至少分配 **2GB** 的記憶體 [Opcache PHP模組](https://www.php.net/manual/en/book.opcache.php). OPcache模組設定於 `php.ini` 檔案。 若要配置2048 MB的記憶體，請設定 `opcache.memory_consumption = 2048`.

## 其他資訊

* [效能最佳實務 — PHP設定](../../../performance/software.md#php-settings)
* [設定PHP選項](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [雲端基礎結構上Adobe Commerce的資料庫最佳實務](database-on-cloud.md)
* [Adobe Commerce中雲端基礎結構最常見的資料庫問題](../maintenance/resolve-database-performance-issues.md)
* [索引器「依排程更新」可最佳化Adobe Commerce效能](../maintenance/indexer-configuration.md)
