---
title: 缓存选项
description: 配置对低级缓存存储的访问。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# 低级缓存选项

商务应用程序使用低级 [缓存](https://glossary.magento.com/cache) [前端](https://glossary.magento.com/frontend) 和 [后端](https://glossary.magento.com/backend) 提供对缓存存储的访问。

## 低级前端缓存

商务扩展 [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) 通过 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 前端缓存。

## 低级后端缓存

通常，商务应用程序可与任何 [Zend_Cache后端](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) 支持。 但是，本指南仅涵盖以下低级后端缓存：

- [雷迪斯](config-redis.md)
- [数据库](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- 文件系统（默认）：使用文件系统缓存无需配置。

[清漆](config-varnish.md) 无需设置低级缓存后端。
