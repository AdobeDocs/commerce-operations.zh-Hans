---
title: 配置缓存
description: 了解缓存以及如何为Adobe Commerce和Magento Open Source应用程序配置缓存机制。
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# 配置缓存

[!DNL Commerce] 允许您配置默认文件系统缓存的替代选项。 本指南讨论了其中一些备选方案；即

- 设置以下内容 [缓存](https://glossary.magento.com/cache) 机制 [!DNL Commerce] 配置：

   - [数据库](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [雷迪斯](config-redis.md)
   - 文件系统（默认）：使用默认文件系统缓存无需配置。

- 设置 [清漆](config-varnish.md) 而不修改 [!DNL Commerce] 配置。

## 缓存术语

[!DNL Commerce] 使用以下缓存术语：

- **弗朗滕** — 类似于缓存存储的接口或网关，由 [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **缓存类型** — 可以是 [!DNL Commerce] 或者 [创建您自己的](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **后端** — 指定有关 [缓存存储](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)，由实施 [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **两级后端** — 将缓存记录存储在两个后端：速度更快，速度更慢。

   >[!INFO]
   >
   >两级后端缓存配置不在本指南的范围之内。

## 配置选项

- 修改提供的 `default` 缓存前端 — 

   您仅修改 `<magento_root>/app/etc/di.xml` 文件，商务应用程序的全局 [依赖注入](https://glossary.magento.com/dependency-injection) 配置。

- 配置您自己的自定义缓存前端 — 

   您仅修改 `<magento_root>/app/etc/env.php` 文件，因为它会覆盖 `di.xml` 文件。

>[!TIP]
>
>清漆不需要对 [!DNL Commerce] 配置。 请参阅 [配置和使用清漆](config-varnish.md).
