---
title: 快取選項
description: 設定對低階快取儲存體的存取權。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 低階快取選項

Commerce應用程式會使用低階快取前端和後端來提供對快取儲存區的存取權。

## 低階前端快取

商務延伸 [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) 透過實作 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 前端快取。

## 低階後端快取

一般而言，Commerce應用程式適用於具有下列條件的任何後端快取： [Zend_Cache後端](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) 支援。 不過，本指南僅涵蓋下列低階後端快取：

- [Redis](config-redis.md)
- [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- 檔案系統（預設）：不需要設定即可使用檔案系統快取。

[清漆](config-varnish.md) 不需要設定低階快取後端。
