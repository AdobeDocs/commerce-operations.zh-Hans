---
title: 設定快取
description: 瞭解快取以及如何設定Adobe Commerce和Magento Open Source應用程式的快取機制。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# 設定快取

[!DNL Commerce] 可讓您設定預設檔案系統快取的替代方案。 本指南會說明其中部分替代方案，即

- 在中設定下列快取機制 [!DNL Commerce] 設定：

   - [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - 檔案系統（預設）：使用預設檔案系統快取不需要任何設定。

- 設定 [清漆](config-varnish.md) 而不修改 [!DNL Commerce] 設定。

## 快取術語

[!DNL Commerce] 會使用以下快取術語：

- **前端** — 類似於快取儲存的介面或閘道，實作者為 [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **快取型別** — 可以是隨附的型別之一 [!DNL Commerce] 或者，您可以 [建立您自己的](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **後端** — 指定以下專案的詳細資訊： [快取儲存體](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)，實作者 [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **兩級後端** — 將快取記錄儲存在兩個後端：快一個和慢一個。

   >[!INFO]
   >
   >兩級後端快取設定不在本指南的涵蓋範圍內。

## 設定選項

- 修改提供的 `default` 快取前端 — 

   您僅可修改 `<magento_root>/app/etc/di.xml` 檔案，Commerce應用程式的全域相依性插入設定。

- 設定您自己的自訂快取前端 — 

   您僅可修改 `<magento_root>/app/etc/env.php` 檔案，因為它會覆寫 `di.xml` 檔案。

>[!TIP]
>
>塗漆不需要變更 [!DNL Commerce] 設定。 另請參閱 [設定及使用清漆](config-varnish.md).
