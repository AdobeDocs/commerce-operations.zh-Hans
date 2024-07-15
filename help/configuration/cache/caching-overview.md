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

[!DNL Commerce]允许您配置默认文件系统缓存的替代项。 本指南将讨论其中一些备选方案，即

- 在[!DNL Commerce]配置中设置以下缓存机制：

   - [数据库](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - 文件系统（默认）：无需配置即可使用默认文件系统缓存。

- 设置[清漆](config-varnish.md)而不修改[!DNL Commerce]配置。

## 缓存术语

[!DNL Commerce]使用以下缓存术语：

- **前端** — 类似于缓存存储的接口或网关，由[Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend)实现。
- **缓存类型** — 可以是随[!DNL Commerce]提供的类型之一，或者您可以[创建您自己的类型](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/)。
- **后端** — 指定有关[缓存存储](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)的详细信息，该存储由[Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)实现
- **二级后端** — 将缓存记录存储在两个后端中：快一个后端，慢一个后端。

  >[!INFO]
  >
  >二级后端缓存配置不在本指南的范围之内。

## 配置选项

- 正在修改提供的`default`缓存前端 — 

  您只修改了`<magento_root>/app/etc/di.xml`文件，即Commerce应用程序的全局依赖项注入配置。

- 配置您自己的自定义缓存前端 — 

  您只修改了`<magento_root>/app/etc/env.php`文件，因为它覆盖了`di.xml`文件中的等效配置。

>[!TIP]
>
>涂漆不需要更改[!DNL Commerce]配置。 请参阅[配置和使用清漆](config-varnish.md)。
