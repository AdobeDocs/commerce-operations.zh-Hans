---
title: 正在安排生产站点上的管理员更新
description: 了解调度Adobe Commerce关键更新以防止性能缓慢和中断的最佳实践。
role: Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# 在生产网站上计划管理员更新的最佳实践

安排在非高峰时间对Adobe Commerce网站进行关键更新和操作，以防止生产网站性能变慢和中断。

关键操作示例：

- 管理员配置更改，例如更新产品属性或将产品子类别移动到另一个类别
- 数据导入或导出操作

关键操作会导致缓存失效和重新索引操作，从而显着增加响应时间，进而可能导致站点中断。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 其他信息

- [缓存最佳实践](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [私有内容：使私有内容无效](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [硬件推荐：缓存](../../../performance/hardware.md#caches)
- [高级设置：设置Redis](../../../performance/advanced-setup.md#set-up-redis)
