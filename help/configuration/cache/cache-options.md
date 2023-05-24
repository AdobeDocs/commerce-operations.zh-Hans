---
title: 缓存选项
description: 配置对低级缓存存储的访问。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 低级缓存选项

Commerce应用程序使用低级缓存前端和后端来提供对缓存存储的访问。

## 低级前端缓存

商务扩展 [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) 通过实施 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 前端缓存。

## 低级后端缓存

通常，Commerce应用程序可与任何后端缓存配合使用，后端 [Zend_Cache后端](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) 支持。 但是，本指南仅涵盖以下低级后端缓存：

- [Redis](config-redis.md)
- [数据库](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- 文件系统（默认）：无需配置即可使用文件系统缓存。

[清漆](config-varnish.md) 不需要设置低级缓存后端。
