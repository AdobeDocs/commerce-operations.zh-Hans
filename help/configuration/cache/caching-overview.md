---
title: 配置缓存
description: 了解缓存以及如何为Adobe Commerce应用程序配置缓存机制。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# 配置缓存

[!DNL Commerce] 使您能够配置默认文件系统缓存的替代项。 本指南将讨论其中一些备选方案，即

- 在中设置以下缓存机制 [!DNL Commerce] 配置：

   - [数据库](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - 文件系统（默认）：无需配置即可使用默认文件系统缓存。

- 设置 [清漆](config-varnish.md) 而不修改 [!DNL Commerce] 配置。

## 缓存术语

[!DNL Commerce] 使用以下缓存术语：

- **前端** — 类似于缓存存储的接口或网关，由实现 [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **缓存类型** — 可以是随提供的类型之一 [!DNL Commerce] 或者，您可以 [创建您自己的](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **后端** — 指定详细信息 [缓存存储](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)，实施者 [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **两级后端** — 将缓存记录存储在两个后端中：一个较快，另一个较慢。

  >[!INFO]
  >
  >二级后端缓存配置不在本指南的范围之内。

## 配置选项

- 修改提供的 `default` 缓存前端 — 

  您只需修改 `<magento_root>/app/etc/di.xml` 文件，Commerce应用程序的全局依赖项注入配置。

- 配置您自己的自定义缓存前端 — 

  您只需修改 `<magento_root>/app/etc/env.php` 文件，因为它覆盖 `di.xml` 文件。

>[!TIP]
>
>涂漆不需要对 [!DNL Commerce] 配置。 请参阅 [配置和使用清漆](config-varnish.md).
