---
title: 缓存选项
description: 了解Adobe Commerce中的低级缓存选项和存储配置。 发现Redis和数据库的前端、后端和存储设置。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# 低级缓存选项

Commerce应用程序使用低级缓存前端和后端来提供对缓存存储的访问。

## 低级前端缓存

Commerce通过实现[Magento\Framework\Cache\Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html)前端缓存来扩展[Zend_Cache_Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)。

## 低级后端缓存

通常，Commerce应用程序可与[Zend_Cache后端](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)支持的任何后端缓存配合使用。 但是，本指南仅涵盖以下低级后端缓存：

- [Redis](config-redis.md)
- [数据库](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- 文件系统（默认）：无需配置即可使用文件系统缓存。

[Varnish](config-varnish.md)不需要设置低级缓存后端。
