---
title: Realpath快取大小
description: 瞭解如何透過更新PHP Readlpath快取設定以使用建議的設定來最佳化Adobe Commerce效能。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Realpath快取設定最佳實務

Realpath快取會快取參照之檔案名稱的真實檔案系統路徑，而非每次都查詢。 每次執行各種檔案功能或需要檔案並使用相對路徑時，PHP都必須查詢該檔案真正存在的位置。

若要改善Commerce效能，請使用以下建議的設定來設定 `realpath_cache` 中的設定 `php.ini` 檔案：

- 將快取大小設定為10 MB (`realpath cache_size=10M`)
- 將存留時間(ttl)設為7200秒(`realpath_cache_ttl=7200`)

如需設定指示，請參閱 [如何設定PHP選項](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## 受影響的產品和版本

- Adobe Commerce內部部署，所有2.3.x版及更高版本
- 雲端基礎結構上的Adobe Commerce，所有2.3.x版及更新版本

## 對效能的潛在影響

如果Realpath快取設定值太低或太高，它會在產生快取時增加額外的負荷，而這會降低效能。

## 其他資訊

- [內部部署： PHP設定](../../../performance/software.md#php-settings)
- 在雲端基礎結構上：
   - [資料庫最佳實務](database-on-cloud.md)
   - [Magento Commerce Cloud中最常見的資料庫問題](../maintenance/resolve-database-performance-issues.md)
- [索引器「依排程更新」可最佳化Magento效能](../maintenance/indexer-configuration.md)
